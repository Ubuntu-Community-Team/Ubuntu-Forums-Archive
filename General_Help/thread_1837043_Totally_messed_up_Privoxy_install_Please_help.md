---
title: "Totally messed up Privoxy install: Please help"
date: 2011-09-01
forum: General Help
---

### Post by vasa1 on 2011-09-01
Linux Newbie on Ubuntu 11.04

I want to use Privoxy purely for content blocking.
I have used it without problems on MS Windows and had installed and used it recently on Mint 11. In both those cases, it "just worked out of the box" and I didn't have to do any preparatory work other than setting up the browser proxy.

But I've made a total mess trying to install it on Ubuntu 11.04 via the Ubuntu Software Centre. I don't want to go into all that I've done but in short,
[LIST]
[*]I installed/removed several times
[*]I messed with the contents of /etc/privoxy trying to replace existing config and user.action files with those that worked for me on Mint 11
[*] I didn't have the presence of mind to save a screenshot of the error message that came up when I tried to use Firefox but it was a standard one of the server refusing connections
[*] I had set up Firefox to use 127.0.0.1 and 8118 as I've done previously on Windows and Mint 11.
[/LIST]
Now, if I try to install via the Ubuntu Software Centre, it tries and then gives me this:

> Package operation failed

The installation or removal of a software package failed.

installArchives() failed: Selecting previously deselected package privoxy.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
...
*stuff deleted by me*
...
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 150859 files and directories currently installed.)
Unpacking privoxy (from .../privoxy_3.0.17-1_i386.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 3 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up privoxy (3.0.17-1) ...
chown: cannot access `/etc/privoxy/user.action': No such file or directory
chown: cannot access `/etc/privoxy/trust': No such file or directory
dpkg: error processing privoxy (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 privoxy
Setting up privoxy (3.0.17-1) ...
chown: cannot access `/etc/privoxy/user.action': No such file or directory
chown: cannot access `/etc/privoxy/trust': No such file or directory
dpkg: error processing privoxy (--configure):
 subprocess installed post-installation script returned error exit status 1


The software center screen now allows me to "remove". After doing that, apparently successfully, I see that /etc/privoxy still exists. It has an (empty) folder called Templates and no other file. (I've set up Nautilus to show hidden files and folders.)

I know that the Ubuntu Software Center isn't "broken" because I could subsequently successfully install other programs, like Audacity.

Any help will be most appreciated. I prefer using Privoxy for content blocking because it can be used with any browser. I'm currently using SimpleBlock for Firefox 6 but making exception rules is not at all easy with that extension.

Edit: This is the text of the error message the browser threw up:
> The proxy server is refusing connections
Firefox is configured to use a proxy server that is refusing connections.
Check the proxy settings to make sure that they are correct.
Contact your network administrator to make sure the proxy server is working. It's just as if Privoxy wasn't installed.

---

### Post by kerry_s on 2011-09-01
i would remove it & start over. use synaptic, mark it for "complete removal" then install it again using synaptic.

then make your changes in /etc/privoxy/config, you'll want to enable the web gui & be able to toggle privoxy on/off.

then run-> sudo service privoxy restart

check-> [http://config.privoxy.org/](http://config.privoxy.org/)
see if it's enabled. see pic

---

### Post by vasa1 on 2011-09-01
> **kerry_s said:**
> i would remove it & start over. use synaptic, mark it for "complete removal" then install it again using synaptic.

then make your changes in /etc/privoxy/config, you'll want to enable the web gui & be able to toggle privoxy on/off.

then run-> sudo service privoxy restart

check-> [http://config.privoxy.org/](http://config.privoxy.org/)
see if it's enabled. see pic

Thank you very much. Your advice worked perfectly. I was quite upset about the whole thing because I really, really like Privoxy.

---

### Post by kerry_s on 2011-09-01
> **vasa1 said:**
> Thank you very much. Your advice worked perfectly. I was quite upset about the whole thing because I really, really like Privoxy.

synaptic is way better, try not to use software center for uninstalling.

---

### Post by vasa1 on 2011-09-01
> **kerry_s said:**
> synaptic is way better, try not to use software center for uninstalling.

I will make a point to do so. As you pointed out, the software center doesn't offer "complete" removal.

---

