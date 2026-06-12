---
title: "What program opens .bin files?"
date: 2009-07-16
forum: General Help
---

### Post by Extreedoc on 2009-07-16
I have a .bin file on my desktop that I need to unlock a BT router, problem is Ubuntu does not recognize it, so what program do I need, any recommendations?

OK, I give up BT I won't unlock the damn router, I'll buy another make, happy now?

Thanks to all who replied, but I know when I am in over my head!!

---

### Post by lisati on 2009-07-16
It depends - some bin files are executable files, others are used to changed settings.

---

### Post by sedawk on 2009-07-16
Try the command "file mybinfile.bin".

This will examine (the header of) the file and give more
information about it.
(In worst case it simply says "data").

Use file with some binaries or image files or media files to get
a feeling for what it shows for different files.
E.g running file on itself:
```

$ type file
file is /usr/bin/file
$ file /usr/bin/file
/usr/bin/file: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV),
for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped

```

---

### Post by binbash on 2009-07-16
Make it executable and run it :

chmod +x asdasd.bin
./asdasdasd.bin

But of course you have to burn the .bin file if it is an image not a binary one

---

### Post by Extreedoc on 2009-07-16
This is the file name: "cfe-voyager220v_sip_bbv-v330r_a2pb021g". File type is described as: "Unknown(application/octet-stream)". I find it curious that it doesn't have an extension such as bin, cue or iso but then again I am not a techie. The only reason I call it a .bin file is because that is how it was described when I downloaded it.
I'm beginning to think that unlocking this router is not such a good idea after all.

---

### Post by t4thfavor on 2009-07-16
It's a cfe (Compact Flash Environment?) image of the router, you would use it on the firmware upload page of your router. Know this though, it can be a one way trip to the garbage heap if you use the wrong one, make sure you know what your doing.


It's like an ISO of a Windows disk for your "BT router", or a snapshot of the OS the router runs.

Make sense?

---

### Post by Extreedoc on 2009-07-16
> **t4thfavor said:**
> It's a cfe (Compact Flash Environment?) image of the router, you would use it on the firmware upload page of your router. Know this though, it can be a one way trip to the garbage heap if you use the wrong one, make sure you know what your doing.


It's like an ISO of a Windows disk for your "BT router", or a snapshot of the OS the router runs.

Make sense?

Thanks for this..., does it make sense to me? Not really, I think I have to learn a lot more before I tackle something like this, I am well out of my depth but thanks to all for your posts, I reckon I'll delete the file and think about another make of router altogether, as I understand it, it is only BT who "lock" their routers. They still behave as if they are a monopoly.

---

### Post by t4thfavor on 2009-07-16
Think of it like updating the firmware on your toaster, oh wait toasters don't have firmware... I don't know, if you plan on staying with BT then you probably need their locked router, in which case you have to leave it alone. If you are moving to another carrier, then your locked BT router is useless and then what could it hurt? If the BT router would be compatible with your new service if it were unlocked, then I would try it, and if it doesn't work trash it.

If you need anymore encouragement, please let me know.

---

### Post by Extreedoc on 2009-07-16
> **t4thfavor said:**
> Think of it like updating the firmware on your toaster, oh wait toasters don't have firmware... I don't know, if you plan on staying with BT then you probably need their locked router, in which case you have to leave it alone. If you are moving to another carrier, then your locked BT router is useless and then what could it hurt? If the BT router would be compatible with your new service if it were unlocked, then I would try it, and if it doesn't work trash it.

If you need anymore encouragement, please let me know.

You are very kind, the thing is I have no idea how to accomplish this task; I know it involves "flashing" and I don't suppose this means dropping my pants, (...but I could be wrong?!) The fact is it wouldn't matter much if the router was scrapped by my efforts as I acquired it for free anyway and my present unlocked BT router is working ok. It was more an experiment that could yield a good working router. The more I read about what is involved, the more I realize my own deficiencies. Is this something that a non-techie should tackle?

I should mention: I'm not with BT, never was.

---

### Post by t4thfavor on 2009-07-16
Login to the web interface, and find the spot that says upgrade firmware. Click browse, and find the cfe file you mentioned earlier. Press go, and wait a while. After that while, reboot the router, and then try to log into it again. If stuff "looks" different, you have succeded, if stuff looks the same, or you cannot login, find a door to hold open with the router, and learn from it.

---

### Post by Extreedoc on 2009-07-17
> **t4thfavor said:**
> Login to the web interface, and find the spot that says upgrade firmware. Click browse, and find the cfe file you mentioned earlier. Press go, and wait a while. After that while, reboot the router, and then try to log into it again. If stuff "looks" different, you have succeded, if stuff looks the same, or you cannot login, find a door to hold open with the router, and learn from it.

Excellent, these are instructions I can follow, together with the help I got from the supplier of the upgrade. I'll give it a go today and let you know whether I've got a working router or a new door stop.
Thank you.

---

### Post by Extreedoc on 2009-07-17
Well, all was going fine, I got to the "Upgrade the firmware button", clicked it and got a demand for "Authentication", User name and password. Well I got the router from someone else so I didn't have them however, wonder of wonders, I managed to get the user name and password from the previous user but still couldn't get in. I wonder if BT have disabled the account?
This is where I am at so far, can't upgrade the firmware because I can't get to the necessary page to do so. Should I give up or is there still a way to triumph over the protectionism of BT?

---

