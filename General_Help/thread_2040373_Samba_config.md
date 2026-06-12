---
title: "Samba config"
date: 2012-08-10
forum: General Help
---

### Post by Kevin Jones on 2012-08-10
Dear all,
I am trying to share  files between two pcs both running ubuntu.
I have followed the instructions from this site:
[https://help.ubuntu.com/11.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/samba-fileserver.html)

Nautilus recognizes the network and 'browse networks icon' shows a windows icon, and both computers. No matter which pc I use clicking on the 'other' pc icon produces this message:
 Unable to mount location.
Failed to retrieve share list from server.

Can anyone tell me what I have to do?

Thanks 
Kevin Jones

---

### Post by sebadamus on 2012-08-10
Hello, I havent read the link you told... but why dont you try installing webmin to configure samba? or gadmin-samba (its a frontend), open it, let it configure its defaults (will rewrite samba.conf), save and restart the service or PC.

You can try in nautilus smb://yoursambaserverip, sometimes I had problems using nautilus network browser, so this way it opens directly.

---

### Post by Morbius1 on 2012-08-11
While I agree with sebadamus that accessing by ip address will probably bypass this problem I can't disagree more about using gadmin-samba. That utility will produce an incoherent mess and few people will be able to help you at that point.

A "Failed to retrieve share list from server" error is usually a machine name resolution problem and the usual suspects are:

[1] Firewalls are in the way. Disable them on your machines and try it again to see if that's the problem.

[2] Services are not started.
On each machine make sure the services are started:
```
sudo service smbd restart
sudo service nmbd restart
```Then wait a few minutes and try to access it again.

[3] Your hostnames are too long.
Run the following command on all your machines and count the number of characters:
```
hostname
```If it's 15 character or less in length then that's not the problem. If it's more than that you can fix it for samba purposes by adding a line to /etc/samba/smb.conf - right under the workgroup line:
```
netbios name = whatever
```[COLOR=Blue]*Just make sure that "whatever" is 15 characters or less in length.*[/COLOR]

Then restart smbd and nmbd again.

[4] Name resolve order is .. well ... in the wrong order:
Add another line  - under the workgroup line again - that looks like this:
```
name resolve order = bcast host lmhosts wins
```And restart smbd and nmbd again.

---

