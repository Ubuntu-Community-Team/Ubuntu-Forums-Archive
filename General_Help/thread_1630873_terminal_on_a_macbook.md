---
title: "terminal on a macbook"
date: 2010-11-25
forum: General Help
---

### Post by LinuxQ on 2010-11-25
Hello all,

I installed ubuntu a few days ago and it was working fine until I restarted the computer.  When I opened the terminal I got this message:

```
bash: /home/me/bin/uname: cannot execute binary file
bash: [: =: unary operator expected
bash: /me/bin/sed: cannot execute binary file
bash: /home/me/bin/ls: cannot execute binary file

```

and when I try to use any other command, I get this message:

```
bash: /home/me/bin/cp: cannot execute binary file

```

I also tried reinstalling Ubuntu and that didn't solve the problem.

I would appreciate it if someone could help me.

Thanks in advance,
LinuxQ

---

### Post by 12apennachi on 2010-11-25
Sounds like you don't have any binaries. That's bad. Unfortunately I have no idea how or why that could have possibly happened.

---

### Post by 12apennachi on 2010-11-25
> **12apennachi said:**
> Sounds like you don't have any binaries. That's bad. Unfortunately I have no idea how or why that could have possibly happened.

Actually, I wonder if you booted a livecd/usb and copied the bin folder into the /usr/ on your hard drive and then booted from the hd like normal. But there are probably more problems than missing binaries.

---

### Post by LinuxQ on 2010-11-25
> **12apennachi said:**
> Sounds like you don't have any binaries. That's bad. Unfortunately I have no idea how or why that could have possibly happened.

I doubt I could find out what the reason is on my own.  How can I restore the binaries?

---

### Post by 12apennachi on 2010-11-25
Do you have a livecd/usb handy?

---

### Post by LinuxQ on 2010-11-25
> **12apennachi said:**
> Do you have a livecd/usb handy?

yes

---

### Post by 12apennachi on 2010-11-25
I am assuming you didn't have any important programs as you only had it for a few days. Try to boot the cd/usb, copy the usr folder from the usb, mount the ubuntu hard drive partition you have on your laptop, and passte it to replace the usr folder there. No guarantees it will work but it's worth a shot.

Edit: Actually, you might as well access the ubuntu partition first to see if anything is there, see what is missing and then try to replace it. Also, it looks like ubuntu is searching for binaries in the home/user/bin folder which does not exist in mine. If it still doesn't work I think you have a much bigger problem than I once expected. You should find someone smarter than me to help you out.

---

### Post by LinuxQ on 2010-11-25
> **12apennachi said:**
> I am assuming you didn't have any important programs as you only had it for a few days. Try to boot the cd/usb, copy the usr folder from the usb, mount the ubuntu hard drive partition you have on your laptop, and passte it to replace the usr folder there. No guarantees it will work but it's worth a shot.

Edit: Actually, you might as well access the ubuntu partition first to see if anything is there, see what is missing and then try to replace it. Also, it looks like ubuntu is searching for binaries in the home/user/bin folder which does not exist in mine. If it still doesn't work I think you have a much bigger problem than I once expected. You should find someone smarter than me to help you out.

Thanks very much for your help, I really appreciate it.  I reinstalled Ubuntu and restated it to see if the problem would occur without installing anything, it didn't.  So it's probably something I installed, I will try to pin it down and see if I can fix it.

thanks again.

---

### Post by 12apennachi on 2010-11-25
Yeah, even though I didn't do much haha. I was just in the shower thinking about this and I realized that I was wrong. I think it was looking in the wrong directory for binary commands. Next time try /bin/uname or /bin/ls etc. That is where default binaries are located, not in usr/bin. I don't knoww what I was thinking.

---

### Post by t4thfavor on 2010-11-25
Sounds like you may have lost your $PATH variable, did you say you could run programs if you typed in the full path, i.e /usr/bin/ls ?

---

