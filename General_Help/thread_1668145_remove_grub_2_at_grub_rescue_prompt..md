---
title: "remove grub 2 at grub rescue prompt."
date: 2011-01-15
forum: General Help
---

### Post by HowBizarre on 2011-01-15
Hello,

So I wanted to get rid of ubuntu 10.10 on my HP pavilion dv6 laptop as I wanted to make some hd space. Its a dual boot with windows 7. I deleted the ubuntu partition and expanded the windows partition to fill the whole hard drive again. 

When I restarted my laptop I got the "error: no such partition. Grub rescue>" message.

I tried inserting my ubuntu 10.10 boot cd but whenever I boot from the cd I get the exact same grub rescue error. Is it possible to remedy this situation from the error?

I am currently unable to download a windows recovery cd so I'm stuck in the grub rescue page unless its possible to fix this mess from the error prompt.

Any help would be GREATLY appreciated.

---

### Post by wilee-nilee on 2011-01-15
> **HowBizarre said:**
> Hello,

So I wanted to get rid of ubuntu 10.10 on my HP pavilion dv6 laptop as I wanted to make some hd space. Its a dual boot with windows 7. I deleted the ubuntu partition and expanded the windows partition to fill the whole hard drive again. 

When I restarted my laptop I got the "error: no such partition. Grub rescue>" message.

I tried inserting my ubuntu 10.10 boot cd but whenever I boot from the cd I get the exact same grub rescue error. Is it possible to remedy this situation from the error?

I am currently unable to download a windows recovery cd so I'm stuck in the grub rescue page unless its possible to fix this mess from the error prompt.

Any help would be GREATLY appreciated.

you can use the lilo boot loader from the ubuntu cd.
[B]
Restore basic windows boot loader - universe enabled[/B]
```
sudo apt-get install lilo
```
then
```
sudo lilo -M /dev/sda mbr
```
**May show error messages about the rest of lilo missing, ignore, we just want MBR**

Make sure your HD is sda look at gparted on the live cd to confirm this, no partitions just sda or what your HD shows.

---

### Post by HowBizarre on 2011-01-15
I can't boot from the ubuntu cd for some reason, whenever I try it takes me to the grub recovery error.

---

### Post by wilee-nilee on 2011-01-15
> **HowBizarre said:**
> I can't boot from the ubuntu cd for some reason, whenever I try it takes me to the grub recovery error.

There is a out of the bios boot menu key prompt. Mine is f12.

---

### Post by HowBizarre on 2011-01-15
I've tried everything. No luck.

---

### Post by wilee-nilee on 2011-01-15
> **HowBizarre said:**
> I've tried everything. No luck.

So this statement does not help me help you, what is everything?

Did you figure out the key prompt I suggested, do you know what I'm talking about?

Is the cd a confirmed working copy?

Have you tried booting something else with it? Or is it actually working? IE the cd/dvd reader

Have you considered loading Ubuntu to a thumb drive if the computer can boot from one.

I think, if it is a good cd and everything else is working it is the boot menu I suggest with the key prompt at powering on, not the bios prompt that is the answer here.

---

### Post by HowBizarre on 2011-01-15
I'm sorry. Didn't mean to be immature about it. And I greatly appreciate your help.

I tried finding the "key prompt", and no such luck. There is a system recovery option(f 11) but whenever I try it it brings me back to the same error.

The CD is a working copy as far as I know, as it is what I used to install ubuntu 10.10

Unfortunately, I cannot test out the thumb drive idea, as my laptop is the only computer available to me at this moment.

Is there anyway I can say restore the system to factory default?

---

### Post by wilee-nilee on 2011-01-15
> **HowBizarre said:**
> I'm sorry. Didn't mean to be immature about it. And I greatly appreciate your help.

I tried finding the "key prompt", and no such luck. There is a system recovery option(f 11) but whenever I try it it brings me back to the same error.

The CD is a working copy as far as I know, as it is what I used to install ubuntu 10.10

Any suggestions?

No problem what is the computer model all I can do is look on google for seesion boot prompt with the model, usually can be found though. The key can be any f key or the esc, HP is f9, Asus is esc, generally.

---

### Post by HowBizarre on 2011-01-16
Hp pavilion dv6.

---

### Post by wilee-nilee on 2011-01-16
> **HowBizarre said:**
> Hp pavilion dv6.

Try f9 while I look for more information.

---

### Post by HowBizarre on 2011-01-16
Okay, so after 10 or so restarts, the boot CD finally worked.

I'm now in ubuntu 10.10.

I did what you told me in my first post and I got this :

"Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated."

Now what?

---

### Post by wilee-nilee on 2011-01-16
> **HowBizarre said:**
> Okay, so after 10 or so restarts, the boot CD finally worked.

I'm now in ubuntu 10.10 so what can I do now to fix this whole situation?

Post 2; has the commands and the instructions to confirm with gparted that the HD is sda.

Read carefully as you seem to be flustered or something this is not that hard and you should be aware of this post already.:)

Te 2 commands are for loading the lilo bootloader to the MBR=master boot record.

---

### Post by HowBizarre on 2011-01-16
check my edited post.

---

### Post by wilee-nilee on 2011-01-16
> **HowBizarre said:**
> check my edited post.

If you ran those two commands and see if it goes to windows.

---

### Post by HowBizarre on 2011-01-16
It worked.

Thank you very much kind sir.

---

### Post by wilee-nilee on 2011-01-16
> **HowBizarre said:**
> It worked.

Thank you very much kind sir.

Cool, have a great year.:)

---

