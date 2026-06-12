---
title: "Real time remote editing of files using ssh/sftp"
date: 2011-12-21
forum: General Help
---

### Post by NahsiN on 2011-12-21
[SIZE=2]Hello all, is it possible to remote edit a file in Kubuntu? Using Nautilus (in Ubuntu)  it was simple. Connect to server, open the file in a text editor, edit  it, save it and it is saved automatically to the remote location. 

But using dolphin it  is not so simple, I managed to connect to my ssh server but when I open  a file, edit it and then save it it says in emacs (or any other text editor) "Wrote  /var/tmp/kdecache-username/krun/4763.0.filename". So my file gets saved to a location on my local machine and not my remote machine. Even more annoying is that when I close the  text editor does KDE give me the option to upload my edited file. This is very  inconvenient. Any suggestions on how can I edit the file in real time? 

Thank you for reading! Any help is appreciated! 

[/SIZE]

---

### Post by NahsiN on 2012-01-06
Thanks to another user over on kubuntuformus the command >  kate sftp://<username>@<IP>/<file path>  works well when launched from terminal for the remote editing task.  But I am still puzzled on how to get remote editing working with emacs. Just replacing 'kate' with 'emacs' in the above syntax unfortunately did not produce the desired result. Any suggestions?

---

### Post by HermanAB on 2012-01-06
$ ssh -C -c arcfour128 -X user@ipaddress "gedit /etc/fstab"

---

### Post by zero2xiii on 2012-01-06
> $ ssh -C -c arcfour128 -X user@ipaddress "gedit /etc/fstab"

That will work. Somewhat "hightech". An easier and more userfriendly-ish way I do this is using the following command:

```
ssh -C -Y user@ipadress
```

This starts an x11 supported session, so you then can run (almost) any gui application ON the remote machine and DISPLAY it localy. This works for the stuff I do. Maybe give it a try? If the connection is very slow, this might not be a feasable option. also note that there is no encryptions specified, so nothing will be encrypted under the ssh stream.

Cherz

---

### Post by NahsiN on 2012-01-07
Thank you Herman and zero2xii for your suggestions. Herman I tried your command and it does work albeit a bit slow. As for zero2xii command, well it does get me into the ssh session but when I launch an application say gedit an error is displayed. It doesn't launch. But nonetheless both approaches rely on X11 forwarding and yes my ssh connection is a bit too slow for that. Any other thoughts? 

I could do it nautilus perfectly. Connect to Server and then launch a file using any text editor and it would do real time editing. The problem only started when I installed Kubuntu and used Dolphin. Any ideas what terminal commands nautilus was using for this task?

Thank you.

---

