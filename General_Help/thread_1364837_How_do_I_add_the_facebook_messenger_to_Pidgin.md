---
title: "How do I add the facebook messenger to Pidgin?"
date: 2009-12-26
forum: General Help
---

### Post by kevinwmiller on 2009-12-26
I want Facebook Messenger on Pidgin.  They had it integrated with the default Mint install.

How do I get it added?

---

### Post by NFblaze on 2009-12-26
Read about it here [http://code.google.com/p/pidgin-facebookchat/]("http://code.google.com/p/pidgin-facebookchat/")

---

### Post by Odin Overland on 2009-12-26
[FONT=Verdana][COLOR=Black]Copy and paste these commands into the terminal one at a time:

"[COLOR=#c20cb9]**wget**[/COLOR] http:[COLOR=#000000]**//**[/COLOR]pidgin-facebookchat.googlecode.com[COLOR=#000000]**/**[/COLOR]files[COLOR=#000000]**/**[/COLOR]pidgin-facebookchat-1.65.deb"
[FONT=monospace]
"[/FONT][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**dpkg**[/COLOR] [COLOR=#660033]-i[/COLOR] pidgin-facebookchat-1.65.deb"

This is the up-to-date version with instructions originally found here:
[/COLOR][/FONT][http://ubuntuguide.net/install-facebook-chat-plugin-for-pidgin-in-ubuntu](http://ubuntuguide.net/install-facebook-chat-plugin-for-pidgin-in-ubuntu)

Pasting the commands into the terminal (without the quote marks of course) is the easiest way to install the package.  Then you start up Pidgin and add in your facebook account.

*(Have edited to put in the newest version)

---

