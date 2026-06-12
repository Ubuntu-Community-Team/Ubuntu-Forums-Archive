---
title: "ubuntu dropped to grub"
date: 2011-10-19
forum: General Help
---

### Post by csyandrews on 2011-10-19
at the risk of sound like an idiot i shall speak my mind. i run Wubi on windows vista whilst in ubuntu upgrade manager did it's thing and i rebooted, after choosing to boot ubuntu i was given a grub command line. at least that's what i think it is it says gnu grub version 1.98-1ubuntu6 if that makes a difference. i think the ubuntu version is 10.04 but i am unsure and can't figure out how to find out. sorry i must sound like a complete tard.

---

### Post by garvinrick4 on 2011-10-19
> **csyandrews said:**
> at the risk of sound like an idiot i shall speak my mind. i run Wubi on windows vista whilst in ubuntu upgrade manager did it's thing and i rebooted, after choosing to boot ubuntu i was given a grub command line. at least that's what i think it is it says gnu grub version 1.98-1ubuntu6 if that makes a difference. i think the ubuntu version is 10.04 but i am unsure and can't figure out how to find out. sorry i must sound like a complete tard.
I do not or any Ubuntu user think you are a tard (do not even know what a tard is) If you are going to
run a WUBI install I would put WUBI in the title or your Threads. There are users who specialize in 
WUBI and will get to your thread as quick as possible. Do not start a new one now, there will be a WUBI
user get to you. I will keep an eye on this and if get know response will get to a WUBI user for you and
ask to help you.
Two of the best are bcbc and rubi1200 I will see if I can get one for you.

---

### Post by csyandrews on 2011-10-19
Thank you, tard is and abbreviation of retard often used in my family,

---

### Post by bcbc on 2011-10-19
Check this out: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

It's the most likely cause of the symptoms you are experiencing.

---

### Post by garvinrick4 on 2011-10-19
> **csyandrews said:**
> Thank you, tard is and abbreviation of retard often used in my family,
I think over your Life you will find that some people will consider this very offensive, but feel you are a young person and will not berate you about it. When you get the chance to meet these  Human beings and the Family's that Love and care for them I am sure you will find that they are special, very special people, all of them. Have a nice day and enjoy you Ubuntu.

---

### Post by garvinrick4 on 2011-10-19
[@csyandrews]("http://ubuntuforums.org/member.php?u=1474610")
Do not go away from these Forums because of anything I stated. I was just making a personal remark
and do think you actually new any better and wish you to be apart of us at ubuntuforums.org. Enjoy
Ubuntu and welcome. Rick

---

### Post by csyandrews on 2011-10-19
i followed the instructions in the link provided by bcbc, the entire disks folder was indeed missing but i was unable to recover the files. does this mean that they are lost and gone forever?

---

### Post by bcbc on 2011-10-19
> **csyandrews said:**
> i followed the instructions in the link provided by bcbc, the entire disks folder was indeed missing but i was unable to recover the files. does this mean that they are lost and gone forever?

Did you run chkdsk? You need to do this first.

If you ran chkdsk and still nothing, what is the output of (from an administrator command prompt on vista/7 or a normal command prompt on xp):
```
dir /s \found.000
```

PS if you installed on C: look for C:\found.000 but if you installed on another drive e.g. X: it will be X:\found.000

---

### Post by csyandrews on 2011-10-19
i did run chkdsk twice just to be sure. 

volume in drive c has no label.
volume serial number is 16b2-65d6

 directory of C:\found.000
10/19/2011  07:10 pm                   0 dir
                        1 files (s)                0 bytes
                        0 Dir (s)     12,948,815,872 bytes free

i did earlier find a couple of things from months ago and containing less then a megabyte

---

### Post by bcbc on 2011-10-19
You have to run chkdsk and set it to fix automatically (this requires a reboot to complete on C: and you have to make sure to let it run to completion).

If you've done this and still nothing, then unfortunately it would seem that the root.disk is gone. I'm not aware of any way to recover any data in this case.

---

### Post by csyandrews on 2011-10-19
right, well i store most stuff in windows so thanks for your help. i will have to reinstall wubi right?

---

### Post by bcbc on 2011-10-19
Yes - reinstall. In that blogpost I mentioned that the loss of the root.disk can be caused by hard poweroffs. If this isn't the cause, I think it might be better to do a regular dual boot. Wubi is great to try out Ubuntu, but it's problems like this one that can make it unsuitable for long term use.

Alternatively if you need to use Wubi for whatever reason, then consider backing up the root.disk from windows every now and then so you can recover easily.

---

