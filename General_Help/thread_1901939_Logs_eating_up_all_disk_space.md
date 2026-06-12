---
title: "Logs eating up all disk space"
date: 2011-12-29
forum: General Help
---

### Post by NilPointer on 2011-12-29
I have problem with logfiles. Three logfiles, that is:

kern.log
messages
syslog

Grown up to 21.2 GB each, making it 63.6 GB total. I don't want to keep them, anyway. It seems just wasting space with millions of lines. Is it safe to clean them and how to do it?

---

### Post by CharlesA on 2011-12-29
They shouldn't be growing that large.

Have you checked them for error messages?

---

### Post by JCM_Pico on 2011-12-29
I had the same problem.... and since it was due to a known issue of my hardware I disabled the log files..... and it worked

Just read to this site [http://www.linuxlog.org/?p=104](http://www.linuxlog.org/?p=104)

---

### Post by NilPointer on 2011-12-29
I've retrieved last 10 lines of file with tail... It seems all three files are filled with lines like that:

```
Dec 30 00:29:32 localhost kernel: [54202.155213] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x37 length 0 status 00000600!
Dec 30 00:29:32 localhost kernel: [54202.155217] eth0: Oversized Ethernet frame f262c370 vs f262c370.
Dec 30 00:29:32 localhost kernel: [54202.155222] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x38 length 2044 status 07fc1519!
Dec 30 00:29:32 localhost kernel: [54202.155227] eth0: Oversized Ethernet frame f262c380 vs f262c380.
Dec 30 00:29:32 localhost kernel: [54202.155378] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x39 length 0 status 00000600!
Dec 30 00:29:32 localhost kernel: [54202.155382] eth0: Oversized Ethernet frame f262c390 vs f262c390.
Dec 30 00:29:32 localhost kernel: [54202.155387] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x3a length 2044 status 07fc1519!
Dec 30 00:29:32 localhost kernel: [54202.155391] eth0: Oversized Ethernet frame f262c3a0 vs f262c3a0.
Dec 30 00:29:32 localhost kernel: [54202.155874] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x3b length 0 status 00000600!
```

Well, seems eth0 causing some problems...

---

### Post by CharlesA on 2011-12-29
Is that machine accessible from the internet?

I saw a [post]("http://forums.gentoo.org/viewtopic-t-149214-highlight-oversized+ethernet+frame.html") where they said that the error may occur if the machine cannot keep up with the data being sent along the PCI bus. The post was from 2004 on Gentoo, so I don't know if it's still applicable.

---

### Post by NilPointer on 2011-12-29
Well, there are 4 forwarded ports, so it might be accessible, but most of time nothing listens to opened ports. But it's definitely not a server.

It's quite strange and explains a lot, that was happening with eth0 (recently it became not too responsible, sometimes totally won't work).

---

### Post by redmk2 on 2011-12-29
> **NilPointer said:**
> I've retrieved last 10 lines of file with tail... It seems all three files are filled with lines like that:

```
Dec 30 00:29:32 localhost kernel: [54202.155213] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x37 length 0 status 00000600!
Dec 30 00:29:32 localhost kernel: [54202.155217] eth0: Oversized Ethernet frame f262c370 vs f262c370.
Dec 30 00:29:32 localhost kernel: [54202.155222] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x38 length 2044 status 07fc1519!
Dec 30 00:29:32 localhost kernel: [54202.155227] eth0: Oversized Ethernet frame f262c380 vs f262c380.
Dec 30 00:29:32 localhost kernel: [54202.155378] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x39 length 0 status 00000600!
Dec 30 00:29:32 localhost kernel: [54202.155382] eth0: Oversized Ethernet frame f262c390 vs f262c390.
Dec 30 00:29:32 localhost kernel: [54202.155387] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x3a length 2044 status 07fc1519!
Dec 30 00:29:32 localhost kernel: [54202.155391] eth0: Oversized Ethernet frame f262c3a0 vs f262c3a0.
Dec 30 00:29:32 localhost kernel: [54202.155874] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x3b length 0 status 00000600!
```

Well, seems eth0 causing some problems...

Indeed!  There are over sized frames being sent to that interface.  The MTU should be 1500 unless you config it to be something else.  This is most likely a LAN problem.  I don't think anybody would send jumbo frames across the Internet.

---

### Post by CharlesA on 2011-12-29
> **NilPointer said:**
> Well, there are 4 forwarded ports, so it might be accessible, but most of time nothing listens to opened ports. But it's definitely not a server.

It's quite strange and explains a lot, that was happening with eth0 (recently it became not too responsible, sometimes totally won't work).
Hrm, I'd put in a new NIC and disable that one and see if the messages go away. It could be that the eth0 NIC is failing and causing problems.

---

### Post by NilPointer on 2011-12-29
I've tried "sudo ifconfig eth0 mtu 1500" and modem reboot.

It's now responding. No new messages were added to logs. So, I'll now clean them and see if new oversized frames will appear. If they will, then really router may be dying.

---

### Post by redmk2 on 2011-12-29
> **NilPointer said:**
> I've tried "sudo ifconfig eth0 mtu 1500" and modem reboot.

It's now responding. No new messages were added to logs. So, I'll now clean them and see if new oversized frames will appear. If they will, then really router may be dying.

You can permanently config that in /etc/network/interfaces.  In the eth0 section as```
mtu 1500
```

Then you can either restart the networking or reboot the machine.

Edit:  But you are right -- you should not have over sized frames coming to eth0 in the first place

---

### Post by NilPointer on 2011-12-30
It seems that log problem is solved. They're not growing (that much) anymore, so oversized packets must've stopped to arrive, too. So, problem is solved... for now.

Thanks for help!

---

