---
title: "Run a php script from the terminal while passing variables"
date: 2012-08-03
forum: General Help
---

### Post by su1 on 2012-08-03
Hi everybody,

I would like to automatize a task I regularly do:

- open a local Wordpress install in Firefox
- access to the settings of a plugin in this Wordpress install
- change the settings of this plugin (through a drop-down list and text field)
- run this plugin, which is a php script that will automatically add images to my posts during a few minutes and will then stop automatically.

I need to do this for multiple local Wordpress sites, and with different plugin settings, so I'd like to integrate that in a small bash script (or other language).

First I thought I could create iMacros for firefox that I would launch from my bash script. The problem is that I must be able to pass variables to my iMacro (the name of the Wordpress site to access, and the settings for the plugin), but I don't think it's possible with iMacro from what I've seen.

I also wanted to use elinks. But 1/ it doesn't seem to be able to run my PHP script (nothing happens when I launch that script from elinks) and 2/ I don't think it's possible to tell elinks via command line: click this link, fill in this form, etc...

There is probably a solution or language to do this that I don't know, so I'm asking for your help here! Any help will be appreciated.

---

### Post by su1 on 2012-08-04
An idea someone?

---

