# iBec Custom Magento 2 Starter Theme

Starter XML layouts, examples of layout and template overrides, theme registration essentials, and folder structure. Intended to be both a functioning starter theme and a miniature example/tutorial for new Magento developers.

### Adapted from LeRoux Kitchen's "iBec Custom" theme

This starter theme inherits Magento's blank theme, in accordance with best practices.

## registration.php and theme.xml
These files define and register the theme with Magento. Theme.xml is where we name the theme and declare Blank as its parent.

### Note related to registration:

When creating a child theme, be sure to put a “logo.svg” in your web/images folder, even if you just want to inherit the default Magento logo. If that file is missing, the child theme will not inherit the styles from the parent. This is contrary to the Magento 2 documentation, which states that the child will inherit the logo if missing/undeclared.

## requirejs-config.js
This file is where we set up custom js dependencies. In this example, this file is necessary to use our custom .js in web/js/main.js

## Magento_Theme/layout/default.xml
This is where you should perform all site-wide layout updates. It inherits the default.xml file from core Blank. Think extending, rather than overriding -- for this reason, our starter theme is mostly full of "remove" actions, removing unused elements from core.

From LeRoux, I've left in some actions related to the footer that I think serve as useful demonstrations of adding new blocks (using the ```Magento\Framework\View\Element\Template``` class and linking them up with templates) and moving elements around.

## Magento_Theme/layout/default_head_blocks.xml
Here's where you can add tags (meta, link, etc) to the \<head\>, site-wide.

**Note: If you want to remove instances certain tags added via default_head_blocks for a particular page, you can use the "remove" action on that page's layout file. Check out this example from Pennington and Bailes:**
```
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
  <head>
    <remove src="js/hotjar.js"/>
  </head>
</page>
```
*(this was checkout_index_index.xml)*

## Other .xml files in Magento_Theme/layout
In the other files here, you'll find examples of layout instructions particular to specific pages. For example, contact_index_index.xml and checkout_index_index.xml each remove the subscription form. On cms_page_view.xml, you'll see a commented-out example of how we added a default OG image to CMS pages on LeRoux

## Other folders
The other folders included in this repo are examples of how to perform core module overrides.

For example, if you needed to edit the core file web/vendor/magento/module-customer/view/frontend/templates/form/register.phtml, you would copy the file and put it here:
Magento_Customer/templates/form/register.phtml

*Note that the format is Vendor_Module, and that in Magento's case "module-customer" just becomes "Customer". Also, note how we're only concerned with the path relative to the "frontend" folder in the core module.

And check out the Magento_OfflinePayments folder to see how to override core modules in a "web" folder, comparing this folder structure to Magento_Customer*

## \_extend.less
Dump all of your LESS/CSS here. Magento will take care of it from here.
