---
title: "Ld_library_path"
date: 2010-02-24
forum: General Help
---

### Post by Sikandar on 2010-02-24
i have to run server side of usbip; the thing that matters is at the time of compiling a project my libusbip.so.0.0 and some more files are getting stored in /usr/local/lib where as it should be in /usr/lib
so i used:
 [B]export LD_LIBRARY_PATH
LD_LIBRARY_PATH=$LD_LIBRARY_PATH/usr/local/lib
 
./configure --prefix=/usr
 
make install[/B]
but am getting the same error as i was getting without LD_LIBRARY_PATH, error is:
usbip err: stub_server.c: 433 (do_standalone_mode) open usb.ids
sir said that its an open error getting due to some privilages problem as am using sudo.
So either LD_LIBRARY_PATH should set it or entering as root.
I want to do it with LD_LIBRARY_PATH.
I am using LD_LIBRARY_PATH for the first time am sure am missing out something.
Is that the right way to use?

---

### Post by Sikandar on 2010-02-24
I have made the device as exportable before this.
meaning i just have to make some changes in usr/local/lib using LD_library_path
as usbipd -D is earlier step to exporting a device.
So reply soon people.

---

### Post by Sikandar on 2010-02-25
Does anyone ever reply to newbies threads over here?????????????
I really doubt.. the matter is ppl like me are just new to linux otherwise we wouldn't have asked for any favour. I suppose this is to easy for them who has been using it since long time.
So the matter of fact is;all those who know how to fix this up, there is no need to feel that its a big deal.
If you cant help others and share your knowledge; let me tell you one thing that you are good for nothing and just an unnecessary burden on this universe.

---

### Post by rnerwein on 2010-02-25
hi
==> [B]LD_LIBRARY_PATH=$LD_LIBRARY_PATH/usr/local/lib
 [/B]
you are missing the ":" ( i don't know the englis[B]h word for : )

LD_LIBRARY_PATH=$LD_LIBRARY_PATH[COLOR=Red]:[/COLOR][/B]/usr/local/lib
export [B]LD_LIBRARY_PATH

ciao

[/B]

---

### Post by Sikandar on 2010-02-25
English word for** :** is **colon**.
Thanks for the reply but its still not working,am getting the same error.
May be am suppose to carry out some more steps.

---

### Post by Sikandar on 2010-02-27
Problem is not fixed yet.

---

