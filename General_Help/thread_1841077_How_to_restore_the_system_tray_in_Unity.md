---
title: "How to restore the system tray in Unity"
date: 2011-09-08
forum: General Help
---

### Post by kaimi&#326;iece on 2011-09-08
I have Ubuntu 11.04, and I want to whitelist everything in the system tray, and I've tried running this:

gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

Also this:

gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

It didn't do anything. Trying to run dconf-editor gets me this:

$ dconf-editor
No command 'dconf-editor' found, did you mean:
 Command 'gconf-editor' from package 'gconf-editor' (main)
dconf-editor: command not found

In gconf-editor there's no settings for Unity.

What gives? I can't use DavMail now, because its configuration panel can only be accessed from the tray. I managed to whitelist the tray icons on a different 11.04 machine before, but on this it just doesn't work.

---

### Post by raj_k on 2011-09-24
Hi
I run the following command in terminal:
  
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

and then LOG OFF and LOG in. Now try out some applications that use systray.

This is my First Post here:)

Raj

---

### Post by raja.genupula on 2011-09-24
> **kaimi&#326 said:**
> I have Ubuntu 11.04, and I want to whitelist everything in the system tray, and I've tried running this:

gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

Also this:

gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

It didn't do anything. Trying to run dconf-editor gets me this:

$ dconf-editor
No command 'dconf-editor' found, did you mean:
 Command 'gconf-editor' from package 'gconf-editor' (main)
dconf-editor: command not found

In gconf-editor there's no settings for Unity.

What gives? I can't use DavMail now, because its configuration panel can only be accessed from the tray. I managed to whitelist the tray icons on a different 11.04 machine before, but on this it just doesn't work.

do this to open 

**Alt+F2** to open unity dash 
and then type **gconf-editor**
it will open 

All the best:D

---

### Post by raj_k on 2011-09-24
Yes  install  "*dconf-editor"  *It's even better.  Check out the link below

[http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html](http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html)

Raj

---

### Post by dino99 on 2011-09-24
> **raja.genupula said:**
> do this to open 

 type **gconf-editor**



gconf-editor is ** replaced ** by gsettings/dconf

***** always use updated tools related to the distro used  ******

---

### Post by raja.genupula on 2011-09-24
> **dino99 said:**
> gconf-editor is ** replaced ** by gsettings/dconf

***** always use updated tools related to the distro used  ******

Hey Dino99
          Thanks for this, I will update it .Thank you very much .

---

### Post by kapetr on 2011-10-31
Unfortunately do not work for me :-/

I use sflphone as (best) VoIP SIP client.

It works great - even in U11.10, but when I close the window (Ctrl+W or click the "x" on window) it should get into systray as icon == keep running waiting for calls, ...

So I have try:

[B]gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Update-notifier', 'sflphone-client-gnome']"
[/B]

or

**set com.canonical.Unity.Panel systray-whitelist "['all']"**

(+ re-log of course)

But after close of sflpone client - no systray icon get visible -> I can't get the sflphone window back. The apps is running ( "ps -efH" ), but his GUI interface is in ... 


Please help

P.S.  I run in Unity 2D mode due my old graphic. But in Panel2D is no such whitelist key.

---

### Post by rdarioc on 2012-05-29
Hi kapetr, 

same problem here. Have you perhaps found a solution in the meanwhile?

Thanks in advance

---

### Post by kapetr on 2012-06-27
In U12.04 it works - after allowing it as described.

---

