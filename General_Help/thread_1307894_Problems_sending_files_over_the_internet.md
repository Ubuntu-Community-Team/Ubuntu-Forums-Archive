---
title: "Problems sending files over the internet"
date: 2009-10-31
forum: General Help
---

### Post by laserbeam on 2009-10-31
Hello everyone... I've been trying for about 50 mins to send a file to a friend of mine and here's what happend:
- pidgin file transfer on yahoo protocol failed (no surprise here)
- my ftp server doesn't work correctly... but that's not really the problem
- jetbytes.com keep crashing (doesn't usualy happen)
- filesovermiles.com didn't work (as i remember it said something abot the firewall blocking it... i don't know what port it uses)
and here starts the fun part...
attaching the file in an email:
- gmail account in evolution mail.... crashed (wtf...)
- gmail and yahoo accounts in firefox - crashed (WHAT THE HELL!!!)
even my system started lagging... gnome do stopped working... htop reported almost no CPU usage...
I don't understand how... but apart from that... i can upload stuff through torrents (which were stopped at the time mentioned above)

what I need:
1) alternate ways to send files
2) figuring out why none of the uploading techniques doesn't work... firewall is permissive for outbound traffic

PS: sorry if i screwed any bit of English in the thread...

---

### Post by XCan on 2009-10-31
Weird, seems like you tried most ways. Perhaps you could also try setting up sshd? After that, if your user can login remotely he should also be able to grab the files through sftp.

---

### Post by laserbeam on 2009-11-01
I'm not going to use ssh of sftp because I'm trying to send files to ordinary folk.

Jetbytes worked today. Ypy.

Although mail still has problems... I don't know why but firefox and prism just seem to crash (or lag really bad and use up resources...). Konqueror managed to attach a file... tho it took like 5-10 minutes and it didn't go through the usual progress bar thingy from yahoo where you see it attaches the files.
It's actually supposed to take some time for a 5 MB file if i think a bit about it... my upload speed isn't that great... but still why does firefox crash? Could some karmic bug influence all these? I actually realized freaky stuff started happening right after i upgraded to a beta version of karmic.

I'll wait a few days... and see if there's any update or so that might fix it...
Thx anyway.

---

