---
title: "Graphics card problem"
date: 2010-10-16
forum: General Help
---

### Post by agkq62 on 2010-10-16
I have a Dell Inspiron laptop running Vista and Ubuntu 9.10. I have tried to do the online upgrade to 10.04 but I just get vertical coloured bars all across the screen so can't see the desktop. Running 10.04 LiveCD give the same problem, 9.10 LiveCD runs fine. It appears 10.04 doesn't like my graphics card.

Any ideas to a solution

---

### Post by sikander3786 on 2010-10-16
Which graphics card?

Press down and hold the Shift key as soon as the laptop gets past the bios screen. You will see Grub menu. Pointing the first entry, press 'e' to edit it. Navigate to the lines "quiet & splash" using the arrow keys, delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot.

What do you get now?

---

### Post by agkq62 on 2010-10-16
Thanks for the reply. Graphics card is ATI Radeon Xpress Series, driver is up to date.

If I modify the grub menu presumably I will still have a problem with the LiveCd.

I really wanted to run the LiveCD as the online upgrade upset the grub menu and also took for ever. I was hoping to load 10.04 in a new partition to see if the change is worthwhile.

Forgot to add because of the problems I have gone back to 9.10

---

### Post by sikander3786 on 2010-10-16
For LiveCD, use the options in the bottom right screen, select nomodeset and boot. You can later make those changes permanent but first make sure if it works or not.

---

### Post by agkq62 on 2010-10-16
Thanks again for the reply. I can't seem to find the options bottom right. When I load the cd I get a page with just  a small icon in the bottom middle then I get the vertical coloured bars.

---

### Post by sikander3786 on 2010-10-17
> When I load the cd I get a page with just a small icon in the bottom middle

If you don't automatically see the page containing options like "Try Ubuntu without making any changes" and "Install Ubuntu" etc etc, pressing any key at the page with small icon and keyboard will do the job. You'll see a menu and then can select nomodeset.

---

### Post by agkq62 on 2010-10-17
Sorry I think I am being very thick. If I press any key I get the language selection page and a list at the bottom for the F keys. F6 is Special Boot Parameters which has listed monitor problems, but I can't find where to select  nomodeset.

---

### Post by agkq62 on 2010-10-17
Right I have found the answer in another post

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameters in this order:

xforcevesa noapic noapci nosplash irqpoll

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa noapic noapci nosplash irqpoll --**

Now hit Enter and hopefully you will be at the desktop admiring Lucid Lynx 10.04




I have 10.04 installed and if i modify the grub to nomodeset everything works.

How do I make the change permanent?

Thanks

---

### Post by sikander3786 on 2010-10-18
> How do I make the change permanent?

Edit /etc/default/grub by

```
sudo gedit /etc/default/grub
```

You'll see

```
GRUB_CMDLINE_LINUX=""
```

Type nomodeset in between those quotation marks "". And now run

```
sudo update-grub
```

in order to update the Grub configuration.

---

### Post by agkq62 on 2010-10-18
Thanks for your patience I thought I was getting there. I followed the instructions and everything loaded fine however after a few minutes web use the coloured bars suddenly return and I have to do a restart.

---

### Post by claven123 on 2010-10-18
Is this for grub or grub2?

---

### Post by agkq62 on 2010-10-18
> **claven123 said:**
> Is this for grub or grub2?

It says Grub 1.98-1ubuntu5 if that is what you mean.

---

### Post by claven123 on 2010-10-18
So, I did the hit e at the grub2 screen and then saw the code....  I replaced the quiet splash with nomodeset and it booted up.

Now, to get the darn video drivers to work.....

---

