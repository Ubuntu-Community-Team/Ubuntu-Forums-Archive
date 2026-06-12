---
title: "Remote Desktop between Ubuntu 9.10"
date: 2010-04-19
forum: General Help
---

### Post by ksaul on 2010-04-19
My office uses ubuntu, as does my home computer. I would like to use remote desktop between the to but not sure how to set it up, any help would be appreciated.

Thanks.

---

### Post by HermanAB on 2010-04-19
Easy, install ssh-server package, forward port 22/TCP in your routers and then do:
ssh -C -c blowfish -X user@ipaddress gnome-panel

and then you can put that panel on the side of your screen and go click happy with the remote system programs running transparently on the local desktop.

---

### Post by ksaul on 2010-04-19
> **HermanAB said:**
> Easy, install ssh-server package, forward port 22/TCP in your routers and then do:
ssh -C -c blowfish -X user@ipaddress gnome-panel

and then you can put that panel on the side of your screen and go click happy with the remote system programs running transparently on the local desktop.

which package? I am an ubuntu newbie

---

### Post by nothingspecial on 2010-04-19
```
sudo apt-get install openssh-server
``` on the machine you want to connect to.

You will need a static ip address - see [COLOR="Red"][here]("http://www.dyndns.com/")[/COLOR]

If you are concerned about security, which your work should be if not you, you might want to look into keys - see [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

Then you access the machine with the syntax posted above.

---

### Post by ksaul on 2010-04-19
> **HermanAB said:**
> Easy, install ssh-server package, forward port 22/TCP in your routers and then do:
ssh -C -c blowfish -X user@ipaddress gnome-panel

and then you can put that panel on the side of your screen and go click happy with the remote system programs running transparently on the local desktop.

so my command line would be

ssh -C -c blowfish -X [email]ksaul@my.dyndns.org[/email] gnome-panel

right?

---

### Post by 2hot6ft2 on 2010-04-19
See the guide in my signature below. Fast and secure.

---

### Post by gatorbrit on 2010-04-20
Hi - I followed your howto - and it works great - I am able to access my machine, but when I connect remotely using qtnx to view my server desktop I don't see the programs that I have running - it is like i have login on it. I'd like to be able to access my existing (running) desktop.

Thks

---

### Post by 2hot6ft2 on 2010-04-20
> **gatorbrit said:**
> Hi - great how to.   But (!) when I connect remotely using qtnx to view my server desktop I don't see the programs that I have running - it is like i have login on it.   I'd like to be able to access my existing (running) desktop.

Thks
Thanks.
qtnx? Can't place off hand what that is.
I'm not sure what would need to be changed to view the desktop that is already running but I believe it's in the node.conf file in shadowing (shadowing a running session).
On the server you can edit the file and try some variations of setting to find out what will allow that by running
```
gksu gedit /etc/nxserver/node.conf
```
It has a lot of things you can change.

Since I'm using it to access my desktop while I'm away there is nobody there so no reason to need to see the running desktop session.

If you figure out what to change in the node.conf file let us know as I'm sure others want to do that too.

There is a lot of documentation on their site here that I haven't had time to go thru and see just what all it can do:
[http://www.nomachine.com/documents.php](http://www.nomachine.com/documents.php)

From what I'm seeing it looks like RDP or VNC would need to be ran within FreeNX.
[http://www.nomachine.com/configuration.php](http://www.nomachine.com/configuration.php)
[http://www.nomachine.com/ar/view.php?ar_id=AR06E00469](http://www.nomachine.com/ar/view.php?ar_id=AR06E00469)

Others trying to get it to work that way
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1327584](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1327584)

---

### Post by ksaul on 2010-04-20
I can connect to my machine with the ssh blowfish posted above, but when it askes for a password (which i assume is my login screen password for the ssh machine?) it says its incorrect.

What do i have to edit/change?

---

### Post by 2hot6ft2 on 2010-04-21
> **gatorbrit said:**
> Hi - I followed your howto - and it works great - I am able to access my machine, but when I connect remotely using qtnx to view my server desktop I don't see the programs that I have running - it is like i have login on it. I'd like to be able to access my existing (running) desktop.

Thks
I figured out how to shadow the servers desktop with FreeNX. And I'm adding it to the guide now.

On the server you need to edit the node.conf file so run
```
gksu gedit /etc/nxserver/node.conf
```
Under this section
###############################################
# Restriction directives
###############################################

Change these 3 by uncommenting them.
From this
```

#ENABLE_DESKTOP_SHARING=1
#ENABLE_SESSION_SHADOWING_AUTHORIZATION=0
#ENABLE_INTERACTIVE_SESSION_SHADOWING=1

```
To this
```

ENABLE_DESKTOP_SHARING=1
ENABLE_SESSION_SHADOWING_AUTHORIZATION=0
ENABLE_INTERACTIVE_SESSION_SHADOWING=1
```

And whatever else you want.

Then in the NX Client go to Configure and set (everything is the same as in the guide except).
Desktop: Set to Shadow

You'll have to play with the screen size a little but you can resize it once it's open.

When you click on Login you will get a Available sessions window.
Try the top one first and click on Attach.
if that doesn't work try the next one.
That's it.

:guitar:

---

### Post by ksaul on 2010-05-06
Upgraded to Lucid and now getting this whenever I try the blowfish method.

> 
** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:22801): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name


---

### Post by ksaul on 2010-05-06
anyone??

---

### Post by ksaul on 2010-05-07
Id love to beable to connect to my computer right about now ):P

any help please?

---

