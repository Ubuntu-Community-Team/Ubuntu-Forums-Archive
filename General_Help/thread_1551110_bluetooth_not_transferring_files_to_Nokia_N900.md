---
title: "bluetooth not transferring files to Nokia N900"
date: 2010-08-11
forum: General Help
---

### Post by quixote on 2010-08-11
The computer and phone are paired, and transfer starts, but after 4096 bytes it says: Transfer finished with an error: Error sending object.  I'm running 64-bit Lucid and Maemo 5 on the phone. Here are some of the things I've tried, following the docs, and the errors I get:
```
~$hcitool info 3D:F7:2A:60:7A:40
Requesting information ...
Can't create connection: Operation not permitted
```[Oops. :redface:.  If I run that as sudo, it gives all the information.]
  
```
~$ bluetooth-sendto
** (bluetooth-sendto:2229): DEBUG: Unhandled UUID 00005005-0000-1000-8000-0002ee000001 (0x5005)
** (bluetooth-sendto:2229): DEBUG: Unhandled UUID 00005601-0000-1000-8000-0002ee000001 (0x5601)
``` The above command opens a nautilus window where I choose a file, it shows my phone as an option to send to which I select and hit send. It says "connecting", the phone makes a little tone to show something is happening and then after about 2 seconds is says "error sending object".  The DEBUG error message appears only in the terminal.

```
~$ /usr/share/doc/obexd-client/examples/send-files 3D:F7:2A:60:7A:40 /home/quixote/dwnlds/audio/In\ the\ Heart\ of\ the\ Moon/12\ Hawa\ Dolo.mp3
Transfer started
  Filename = /home/quixote/dwnlds/audio/In the Heart of the Moon/12 Hawa Dolo.mp3
  Name = 12 Hawa Dolo.mp3
  Size = 12030316
Transfer progress (0 bytes)
Transfer progress (4096 bytes)
Transfer finished with an error: Error sending object
```Trying that command was just something I saw on a forum somewhere, and it gives a more interesting error message.  But I still have no idea what to try next :( .

---

### Post by quixote on 2010-08-13
buuuump??

---

### Post by tgalati4 on 2010-08-13
You have spaces in your file names.  That might cause a problem in transfering the file.  Try sending a file that does not have spaces in it.

---

### Post by quixote on 2010-08-14
Yes, but the spaces are escaped, and the error messages are exactly the same with no-space filenames.  I tried that because I figured I must not have escaped the spaces properly. 

It seems like, if I knew enough about it, the fact that the transfer starts and then fails about 4K into it should be diagnostic of what the problem is.  ???

---

