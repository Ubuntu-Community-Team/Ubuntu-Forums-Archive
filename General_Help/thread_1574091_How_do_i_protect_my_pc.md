---
title: "How do i protect my pc?"
date: 2010-09-13
forum: General Help
---

### Post by jinba.ittai on 2010-09-13
Today on my way in after a run, i found my room mate on my pc. I had forgotten to lock the screen, but what made me even more mad was the fact that i didnt give her permission even though all she was doing was transferring music to a key drive... she could have went through all my files for all i know. Anyways, Im looking for a way to keep her out of my system. I know there are ways to put passwords on the bios before start up, but my bios seems to be lacking that option. Can someone point me in the right direction? Id also like to make it to where if she put in a live disk, she wouldnt be able to read my hard drives (maybe some disk cryption?) I have a portable hdd so i can back all my stuff up if i need to re install my os(s), windows 7 and ubuntu. Any ideas? It would also be cool to hide grub and make it boot straight into windows without grub prompt. (and have grub show up on an assigned key hit? if possible)

---

### Post by aysiu on 2010-09-13
The only thing close to physical security in terms of effectiveness is encryption.

Try full-disk encryption.

Or get a new roommate? One you trust?

---

### Post by cariboo on 2010-09-13
You didn't say what version you were using, but Lucid automatically locks the screen after 5 minutes of no activity by default. Using a strong password and the default lock screen behavior will keep most **novice/average** users from using your computer.

If your room mate is an experienced Linux user, the only thing to do is encrypt the hard drive as aysiu said and make it a habit of logging out when you leave the system.

---

### Post by endotherm on 2010-09-13
i've been reminded by security gurus on several occasions, that in many cases, a locked door beats every technological protection you could put up.

---

### Post by DogMatix on 2010-09-13
> **endotherm said:**
> i've been reminded by security gurus on several occasions, that in many cases, a locked door beats every technological protection you could put up.

Absolutely, good advice. Remember to log out. Shut the door.

---

### Post by Gunman1982 on 2010-09-13
To prevent the usage of a livecd change the bootorder in your bios to boot from the hdd at first and lock it with a bios password. Only thing your roomy could do then would be to open your computer and disconnect the bios battery to reset it.

Another way would be to encrypt your hdd, but you don't have to encrypt all of it, just your home directory would be enough, at least on linux.

---

### Post by jinba.ittai on 2010-09-13
> **endotherm said:**
> i've been reminded by security gurus on several occasions, that in many cases, a locked door beats every technological protection you could put up.

For some reason or another, my door fails to lock anymore D=

---

### Post by jinba.ittai on 2010-09-13
> **Gunman1982 said:**
> To prevent the usage of a livecd change the bootorder in your bios to boot from the hdd at first and lock it with a bios password. Only thing your roomy could do then would be to open your computer and disconnect the bios battery to reset it.

Another way would be to encrypt your hdd, but you don't have to encrypt all of it, just your home directory would be enough, at least on linux.

Done and done, THNX!

---

### Post by jinba.ittai on 2010-09-13
> **aysiu said:**
> The only thing close to physical security in terms of effectiveness is encryption.

Try full-disk encryption.

Or get a new roommate? One you trust?

Yeah, im working on encrypting it atm, its not that she isnt trust worthy, its just i dont really trust anyone around my computer, catch my drift?

Got any links to some good disk crypts?

---

### Post by CharlesA on 2010-09-13
[TrueCrypt]("http://www.truecrypt.org/") is always good.

---

### Post by valbaca on 2010-09-13
> **jinba.ittai said:**
> Yeah, im working on encrypting it atm, its not that she isnt trust worthy, its just i dont really trust anyone around my computer, catch my drift?

Got any links to some good disk crypts?

The current leader: [http://www.truecrypt.org/](http://www.truecrypt.org/)

For the Linux wrapper:
```
sudo apt-get install easycrypt
```

---

### Post by 7h3d4rk0n3 on 2010-09-23
Encrypt home folder, and TrueCrypt == gg for your roomie. Also, set the computer to lock after 5 min of inactivity.

---

