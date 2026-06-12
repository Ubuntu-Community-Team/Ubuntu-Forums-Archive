---
title: "Make Hotmail default email client"
date: 2009-07-19
forum: General Help
---

### Post by Charbs on 2009-07-19
Does anyone know how to setup hotmail to be the default email client in ubuntu 9.04?

---

### Post by kerry_s on 2009-07-19
just setup the mail program to use hotmail pop.

```
Incoming Server (POP3 Server): pop3.live.com
Incoming Server POP Port: 995
Incoming Server POP SSL Encryption: Yes (On or Required)

Outgoing Server (SMTP Server): smtp.live.com
Outgoing Server SMTP Port: 25
Outgoing Server Authentication: Yes (On &#8211; Use POP username and password or Hotmail credentials)
Outgoing Server TLS or SSL Secure Encrypted Connection: Yes (On or Required)

User Name: Windows Live ID (e.g. yourname@hotmail.com)
Password: password used to sign in to Hotmail or Windows Live service
```

---

### Post by Charbs on 2009-07-19
Nono, i dont wanna have to use thunderbird or any local email application. I want to be able to click on any link on a website and have it automatically open hotmail in a new tab in firefox and load my email inside the web browser.

---

### Post by Jesus_Valdez on 2009-07-19
Maybe this helps altough it's for Gmail maybe gives you some pointers:

easy one:

[http://ubuntuforums.org/showthread.php?t=1100933&highlight=gmail+default+firefox](http://ubuntuforums.org/showthread.php?t=1100933&highlight=gmail+default+firefox)

Not that easy one:
[http://ubuntuforums.org/showthread.php?t=1037693&highlight=gmail+default+firefox](http://ubuntuforums.org/showthread.php?t=1037693&highlight=gmail+default+firefox)

---

### Post by Charbs on 2009-07-19
ya i saw that website already, its promising, but i dont really know what info to put in to replace the gmail settings for hotmail settings :(

---

### Post by kerry_s on 2009-07-19
> **Charbs said:**
> Nono, i dont wanna have to use thunderbird or any local email application. I want to be able to click on any link on a website and have it automatically open hotmail in a new tab in firefox and load my email inside the web browser.

[http://support.mozilla.com/tiki-view_forum_thread.php?locale=no&comments_parentId=227144&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?locale=no&comments_parentId=227144&forumId=1)

---

### Post by Charbs on 2009-07-19
Cool thanks, ill give that a try later.
That should hopefully make hotmail the default for firefox, but not the default for the entire OS (Ubuntu). but this might be good enough for now.

Thanks

---

### Post by Jesus_Valdez on 2009-07-19
> **SketchyClown said:**
> 

[B]Second:

[/B]In the ***System*** menu on the panel, navigate to ***Preferences > Preferred Applications ***and in the section for ***'Mail Reader' ***, select ***'Custom'*** and in the ***'command' ***box, enter ***'firefox %s' ***(without the quotes, of course).

Thats it. You are now done. No scripts, no command line. Test it out by clicking any link to send an email either in a web page or for example in Emesene/Pidgin Messenger for sending an email to someone and you should find that Firefox opens a compose email window with the recipient's email address there for you.

Enjoy.:D


I guess that should do the trick.

---

