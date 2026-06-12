---
title: "Evolution HTML messages not showing font colors"
date: 2011-01-27
forum: General Help
---

### Post by jkrejci@usinternet.com on 2011-01-27
I have Evolution 2.28.3 running. 
Ubuntu 10.04 LTS (fully patched)

Occasionally people will use colors in their HTML email messages and will put "see below my comments inline are red" or something along those lines. When I get these in Evolution the colors are not displayed at all. The "red" parts are displayed in the same color as the rest of the body. I am using IMAP to connect to the server. If I use another IMAP client like roundcube.net and view the exact same message the colors are visible as expected.

I cannot find any setting within Evolution to control this. I have enabled "view HTML message" and other HTML markups appear to be reflected such as inline images and colors from messages I compose in Evolution. It appears to be only Outlook composed emails possibly? I see they have a bunch more crap in the message source than an equivalent message composed solely within Evolution.

Is there some setting I am missing, possibly within Gnome itself so I can view the message formatting as intended?

---

### Post by gordintoronto on 2011-01-27
In Evolutions' preferences, there are html settings, including turning html off.

---

### Post by jkrejci@usinternet.com on 2011-01-27
I am guessing you read only the message subject and not the body of my post? I have HTML viewing enabled and some/most of the HTML formatting comes thru, just not the font colors of some emails (looks to be MS Outlook messages in particular).

---

### Post by vdoki on 2011-04-21
I have the same in ubuntu 11.04, evolution 2.32.2. This is quite a shame, that an HTML email looks better in windws outlook.

---

### Post by dcstar on 2011-04-21
> **vdoki said:**
> I have the same in ubuntu 11.04, evolution 2.32.2. This is quite a shame, that an HTML email looks better in windws outlook.

There are** no **standards for HTML e-mail, MS makes up things that only work correctly with their products and this is an ongoing problem for other mail clients.

Even the output of newer versions of some MS products won't render correctly in their older mail clients, so they force people to keep upgrading (and therefore spending money) just so these new "features" work correctly.

Evolution supports basic HTML messages, not HTML code that should only be used in browsers.

---

### Post by vdoki on 2011-04-21
I got it. Although the same email looks much better in thunderbird. 

So I just hope, that the webkit integration will be done soon, as I've found here:

[http://live.gnome.org/Evolution/FAQ#Why_does_Evolution_not_correctly_display_some_HTML_emails.3F](http://live.gnome.org/Evolution/FAQ#Why_does_Evolution_not_correctly_display_some_HTML_emails.3F)

---

### Post by apochry on 2011-04-21
> If an HTML mail is not correctly displayed in Evolution it might be that the formatting is specified as CSS. CSS is currently not supported by gtkhtml (the part that Evolution uses to display HTML). This will likely be fixed in version 3.2 when Evolution will use WebKit instead of gtkhtml.
Well, fine, version 3.2 it is. But Ubuntu 11.04 will come with Evolution 2.32.2. According to Evo's [home page]("http://projects.gnome.org/evolution/download.shtml"), the curent stable version is 3.0. Is anyone using it on Ubuntu? Or is it possible to be installed and work properly? I'm asking because I would like to read RSS news in Evolution and the plugin can be used only with later versions of Evo' (2.8+).

Regards,
Izzo

---

