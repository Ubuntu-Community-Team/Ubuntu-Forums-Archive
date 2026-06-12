---
title: "No such file or directory when tring to run"
date: 2011-05-07
forum: General Help
---

### Post by eyalmmm on 2011-05-07
Hello 
im new with linux 
I tried to open a dedicated server for cs 1.6 
but when i download hldsupdatetool.bin 
give privilages 
I try to run but it says "No such file or directory"
it is there i know 

[PHP]
2011-05-07 21:59:52 (75.4 KB/s) - `hldsupdatetool.bin' saved [3513408/3513408]

> chmod +x hldsupdatetool.bin 
> ./hldsupdatetool.bin
bash: ./hldsupdatetool.bin: No such file or directory
[/PHP]

---

### Post by matt_symes on 2011-05-07
Hi

Are you using 64bit Ubuntu ? I seem to remember reading there may be an issue with hldsupdatetool.bin and 64 bit systems because o fthe libraries.

Post the output of (from a terminal)

```
 uname -a
```

It if contains x86_64 then you need to get the 32 bit libraries on your system.

I am not 100% sure about this but i am pretty sure i read it.

Kind regards

---

### Post by eyalmmm on 2011-05-07
> **matt_symes said:**
> Hi

Are you using 64bit Ubuntu ? I seem to remember reading there may be an issue with hldsupdatetool.bin and 64 bit systems because o fthe libraries.

Post the output of (from a terminal)

```
 uname -a
```

It if contains x86_64 then you need to get the 32 bit libraries on your system.

I am not 100% sure about this but i am pretty sure i read it.

Kind regards

thank u but it doesnt work and im working on linux server

> Linux Eyal 2.6.38-8-server #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

where do i get the liberies

---

### Post by matt_symes on 2011-05-07
Hi

> **eyalmmm said:**
> thank u but it doesnt work and im working on linux server

What doesn't work ? 

Kind regards

---

### Post by eyalmmm on 2011-05-07
i mean i dont know what to do can u please help me

---

### Post by matt_symes on 2011-05-07
Hi

If you are using Ubuntu 11.04 server then log onto the console.

Type 

```
uname -a
```

and hit enter. What ever is displayed on your server type into your next post so i can see the results of the command.

This will tell me if you are using a 32 or 64 bit Linux kernel and libraries. We can then take it from there.

Kind regards

---

### Post by eyalmmm on 2011-05-07
Linux Eyal 2.6.38-8-server #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Thank u

---

### Post by matt_symes on 2011-05-07
Hi

> Linux Eyal 2.6.38-8-server #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 x86_64 x86_64 **x86_64** GNU/Linux

As you can see you are using a 64 bit version of Ubuntu. I am pretty sure hldsupdatetool.bin needs the 32 bit libraries to run.

Try this...

```
sudo apt-get install ia32-libs
```

and then try to run your program again.

Kind regards

---

