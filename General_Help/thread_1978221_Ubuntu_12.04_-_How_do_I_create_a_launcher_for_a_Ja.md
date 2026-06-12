---
title: "Ubuntu 12.04 - How do I create a launcher for a Java app"
date: 2012-05-11
forum: General Help
---

### Post by OS Stuntman on 2012-05-11
Hello,            

How do I create a launcher/icon for a Java app. I have it installed and I can launch it in Nautilus, but want to be able to pull it up in dash.   Here's the app: [http://www.ericbt.com/Vault3](http://www.ericbt.com/Vault3), which should be in the Shopping Center, IMO.

---

### Post by kc1di on 2012-05-11
you will need to make a .desktop file and place it in /usr/share/applications folder.

here's how to do it.

[http://askubuntu.com/questions/72535/creating-desktop-files-to-use-on-the-open-with-other-application-tab]("http://askubuntu.com/questions/72535/creating-desktop-files-to-use-on-the-open-with-other-application-tab")

---

### Post by MG&amp;TL on 2012-05-11
Also, you can use the *alacarte* ("main menu") program, which is available in the software centre to make it for you.

Just set the command field to the command used to run the java app.

---

### Post by voodoo123 on 2012-05-11
> **MG&TL said:**
> Also, you can use the *alacarte* ("main menu") program, which is available in the software centre to make it for you.

Just set the command field to the command used to run the java app.

Also to note about this, you will need to log out and back in before it will show up in the Dash. I spent a few minutes figuring this out the first time I did it with 12.04.

---

### Post by psychotix on 2012-05-11
WOW.  This worked for AptanaStudio3 w/o even logging out.

---

### Post by ubialan on 2012-08-26
For a link to a url I simply created a bookmark in my browser and drug it onto my desktop or panel and right clicked selected properties to edit. Too bad  they have to improve things.

---

### Post by ubialan on 2012-08-26
double post

---

