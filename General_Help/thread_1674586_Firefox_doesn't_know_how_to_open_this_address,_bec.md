---
title: "Firefox doesn't know how to open this address, because the protocol (skype) isn't ***"
date: 2011-01-24
forum: General Help
---

### Post by junovo on 2011-01-24
Using Ubuntu 10.04 LTS and Firefox 3.6.13. Created a call me button from the following address [http://www.skype.com/intl/en-us/tell-a-friend/get-a-skype-button/](http://www.skype.com/intl/en-us/tell-a-friend/get-a-skype-button/)

Placed the button on my website and when using Firefox to click on the button i get error : Firefox doesn't know how to open this address, because the protocol (skype) isn't associated with any program.

the HTML used is

<!--
Skype 'Skype Me™!' button
[http://www.skype.com/go/skypebuttons](http://www.skype.com/go/skypebuttons)
-->
<script type="text/javascript" src="http://download.skype.com/share/skypebuttons/js/skypeCheck.js"></script>
<a href="skype:wingusupport?call"><img src="http://download.skype.com/share/skypebuttons/buttons/call_green_white_153x63.png" style="border: none;" width="153" height="63" alt="Skype Me™!" /></a>

How do I instruct Firefox to open Skype 2.1.0.81 already installed and running.

Thanks

---

### Post by peculiar penguin on 2011-01-24
[http://blog.mozilla.com/addons/2011/01/20/blocking-the-skype-toolbar-in-firefox/](http://blog.mozilla.com/addons/2011/01/20/blocking-the-skype-toolbar-in-firefox/)

Check if you have that extension installed and whether it's enabled or disabled?

---

### Post by wojox on 2011-01-24
Try this out [Register protocol]("http://kb.mozillazine.org/Register_protocol")

---

### Post by Phenex1978 on 2011-01-24
It's probably related to the decision of Mozilla to block the Skype add-on

[http://www.ghacks.net/2011/01/21/skype-toolbar-blocked-in-firefox-by-mozilla/](http://www.ghacks.net/2011/01/21/skype-toolbar-blocked-in-firefox-by-mozilla/)

---

### Post by junovo on 2011-01-24
thanks for the replies so far 

I am kind of half way there using the below and changing the foo part with skype. However I have skype running already as a start up and this seems to want to open another session. Any ideas ?


Firefox 3.5 and above
(Works without installed Gnome libraries)
Type about:config into the Location Bar (address bar) and press Enter.
Right-click -> New -> Boolean -> Name: network.protocol-handler.expose.foo -> Value -> false (Replace foo with the protocol you're specifying)
Next time you click a link of protocol-type foo you will be asked which application to open it with.

---

### Post by junovo on 2011-01-27
Anyone ... Help ?? :(

---

