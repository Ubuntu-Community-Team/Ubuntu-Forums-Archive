---
title: "how do you wipe free space in ubuntu?"
date: 2011-02-11
forum: General Help
---

### Post by JuicyCouture on 2011-02-11
securely 

like with windows i would use CCleaner with a DoD 3 pass wipe

how can i do the equivalent of this?

---

### Post by Dark_Stang on 2011-02-11
The package Secure-Delete looks promising.

---

### Post by JuicyCouture on 2011-02-11
thats not popping up in the software center how do i get it?

i read its an actual built in function through the command line

someone help please

---

### Post by Dark_Stang on 2011-02-11
It's probably not in a normal repository. Canonical usually doesn't back things that dangerous.

Open up Software Center. Go Edit > Software Sources.
Make sure the Universe and Multiverse repositories are check. If they aren't, check them and close the window. Software Center should reload it's caches and you should be able to search for it after that.

---

### Post by JuicyCouture on 2011-02-11
> **Dark_Stang said:**
> It's probably not in a normal repository. Canonical usually doesn't back things that dangerous.

Open up Software Center. Go Edit > Software Sources.
Make sure the Universe and Multiverse repositories are check. If they aren't, check them and close the window. Software Center should reload it's caches and you should be able to search for it after that.


its not in there i'll try synaptic

---

### Post by JuicyCouture on 2011-02-11
well it was in synaptic

but its not showing up in my application menu guess i'll have to go search around for it

---

### Post by JuicyCouture on 2011-02-11
i cant find the damn thing! stupid ubuntu

---

### Post by oldos2er on 2011-02-12
The secure-delete package installs four CLI tools; srm, sfill, sswap, and sdmem. Run *man <command>* for info on each one.

---

### Post by steve161 on 2011-02-12
bleachbit is in the repos and has a gui option for a one pass zero overwrite of free space.

---

### Post by JuicyCouture on 2011-02-12
one pass is insufficient

---

### Post by samacaster on 2011-02-12
Look, lets put this to rest now. Whether you run 1 pass, or ten thousand passes, If I'm determined enough, I will recover data. Its that simple. I don't care what OS your running, whether you used CCleaner, Bleachbit, Comodo SystemCleaner, File Shredders, or any combination of "cleaners" out there, the bottom line is this: Nothing is erased, hidden, shredded, Yada-Yada...A computer forensic specialist will beat you every time. Take it to heart. BleachBit writes it's last pass as Zero's to hide the fact that you tried to hide data, good grief! People, you want your hard irrecoverable? Give it the  [I]Gallagher treatment.
[/I]

---

### Post by williamts99 on 2011-02-12
> **JuicyCouture said:**
> securely 

like with windows i would use CCleaner with a DoD 3 pass wipe

how can i do the equivalent of this?

From the command line, install the secure-delete package:
```
sudo apt-get install secure-delete
```

Again from the command line, run:
```
sfill
```

You will see the options that you can use, for the quickest option use:
```
sudo sfill -llz /
```

---

### Post by Andrew.Z on 2011-02-12
> **samacaster said:**
> Look, lets put this to rest now. Whether you run 1 pass, or ten thousand passes, If I'm determined enough, I will recover data. Its that simple. I don't care what OS your running, whether you used CCleaner, Bleachbit, Comodo SystemCleaner, File Shredders, or any combination of "cleaners" out there, the bottom line is this: Nothing is erased, hidden, shredded, Yada-Yada...A computer forensic specialist will beat you every time. Take it to heart. BleachBit writes it's last pass as Zero's to hide the fact that you tried to hide data, good grief! People, you want your hard irrecoverable? Give it the  [I]Gallagher treatment.
[/I]

There is [no credible evidence that any data overwritten a single time can ever be recovered](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk) by anyone in any way.   The only exception is that overwriting free disk space doesn't overwrite all data even once ( for example files that are allocated cannot be wiped).  The link has more details.  If you don't agree, please give a credible citation.

---

### Post by Nixarter on 2011-02-12
> **Dark_Stang said:**
> It's probably not in a normal repository. Canonical usually doesn't back things that dangerous.

Open up Software Center. Go Edit > Software Sources.
Make sure the Universe and Multiverse repositories are check. If they aren't, check them and close the window. Software Center should reload it's caches and you should be able to search for it after that.


What do you mean by "that dangerous?"  Do the available programs corrupt files/drives, or are they otherwise unstable?

As for the topic, if you are wanting to unrecoverably-delete sensitive information from a computer, you're doing (at least) 2 things wrong.  1.  You obviously aren't storing/accessing the sensitive information correctly, and 2.  you are going about deleting it wrong.  The only way to do what you're thinking of correctly is to completely wipe the whole drive, then go back and put things back in (though not from backups, from the original sources/repositories or what-have-you).  There are many, many places for a CC#, SS#, password or whatever to hide on a drive that these programs simply don't check.  Once the data is on a drive, it is safe to assume it is 100% recoverable until and unless the entire drive is properly wiped.

That being said, to save a convoluted explanation, a single-pass is sufficient for your purpose.

---

### Post by techunit on 2011-02-12
> **samacaster said:**
> Look, lets put this to rest now. Whether you run 1 pass, or ten thousand passes, If I'm determined enough, I will recover data. Its that simple. I don't care what OS your running, whether you used CCleaner, Bleachbit, Comodo SystemCleaner, File Shredders, or any combination of "cleaners" out there, the bottom line is this: Nothing is erased, hidden, shredded, Yada-Yada...A computer forensic specialist will beat you every time. Take it to heart. BleachBit writes it's last pass as Zero's to hide the fact that you tried to hide data, good grief! People, you want your hard irrecoverable? Give it the  [I]Gallagher treatment.
[/I]
I disagree however your going to have to do a lot more than just wipe your computer's harddrive. Your going to need to have had your data encryped with at least three layers of high-end algorithms, a dedicated bootloader and at least a 128 charactor password featuring symbals capitals numbers and of course letters. At this point they can still recover data but it will take **hours to days with direct access** if you take the extra step of wiping your harddrive and demagnetizing it you can hope to have killed the possiblilty of recovering data. Just make sure you remove your ram!

---

### Post by techunit on 2011-02-12
> **Nixarter said:**
> What do you mean by "that dangerous?"  Do the available programs corrupt files/drives, or are they otherwise unstable?

As for the topic, if you are wanting to unrecoverably-delete sensitive information from a computer, you're doing (at least) 2 things wrong.  1.  You obviously aren't storing/accessing the sensitive information correctly, and 2.  you are going about deleting it wrong.  The only way to do what you're thinking of correctly is to completely wipe the whole drive, then go back and put things back in (though not from backups, from the original sources/repositories or what-have-you).  There are many, many places for a CC#, SS#, password or whatever to hide on a drive that these programs simply don't check.  Once the data is on a drive, it is safe to assume it is 100% recoverable until and unless the entire drive is properly wiped.

That being said, to save a convoluted explanation, a single-pass is sufficient for your purpose.
You could just store sensitive data in a encrypted volume. When you delete it normally it will still be magetically stored on the harddrive but it will also be less likely to be found or accessed. Of course if they have direct access and powerful enough equipment there is no point.

---

### Post by Nixarter on 2011-02-12
On an encrypted drive, the data is basically pre-deleted.  You lose access to the key, and there is no danger.  It is not practically recoverable.  Your statement about a powerful enough computer is misleading...  It would take all the computers on earth billions of years to go through only 1% of the possible keys, even if the passphrase was known.  (assuming proper implementation)  So no, the data is safe.  That being said, if you are generating keys to try randomly, theoretically it is possible that you get extremely lucky and the very first one you try just happens to be correct.  But that isn't going to happen.

Direct access makes no difference.

The only chance of recovery (again, if implemented properly... and that's a big if) is the RAM.  1.  if they leave the computer on.  Or 2.  If they had the computer on, with the key and passphrase in RAM (for whatever reason) for an extended period of time.  This can cause real physical changes in the RAM that can be read (though not by the computer) long after the computer is turned off (basically forever).  The data would have to be extremely important to even try that method, though (due to expense and the sheer number of "if's").  But, strictly speaking, both of those are actually examples of poor implementation.

---

### Post by williamts99 on 2011-02-12
This is starting to go... well you know.  It is up to the person in charge, usually the owner, which levels of security he has/wants to use.  Lets leave it at that and just provide the tools needed. :)

---

### Post by flipper T on 2011-02-12
can't you just store your porn stash in a folder called "mom, please don't open" ?

---

### Post by Nixarter on 2011-02-12
> **williamts99 said:**
> This is starting to go... well you know.  It is up to the person in charge, usually the owner, which levels of security he has/wants to use.  Lets leave it at that and just provide the tools needed. :)

I don't think it's going off-topic at all.  Yes, it is up to the owner/operator to weigh the odds and choose the level of security he or she wants, and then find the programs and means to match.  The reason I posted was because 1.  There was a lot of misinformation being posted which could easily lead people to misunderstand many things about the topic at hand.  And 2.  The original poster was on a wild goose chase led by false assumptions and misinformation gathered from who-knows-where long before this thread was made.  Without a basic and accurate understanding of the subject (any subject, including this one), nobody can make valid decisions.  Now that the poster is educated enough on the basics, he or she can make decisions and the results of which will be predictable and as desired.

---

### Post by techunit on 2011-02-12
> **Nixarter said:**
> On an encrypted drive, the data is basically pre-deleted.  You lose access to the key, and there is no danger.  It is not practically recoverable.  Your statement about a powerful enough computer is misleading...  It would take all the computers on earth billions of years to go through only 1% of the possible keys, even if the passphrase was known.  (assuming proper implementation)  So no, the data is safe.  That being said, if you are generating keys to try randomly, theoretically it is possible that you get extremely lucky and the very first one you try just happens to be correct.  But that isn't going to happen.

Direct access makes no difference.

The only chance of recovery (again, if implemented properly... and that's a big if) is the RAM.  1.  if they leave the computer on.  Or 2.  If they had the computer on, with the key and passphrase in RAM (for whatever reason) for an extended period of time.  This can cause real physical changes in the RAM that can be read (though not by the computer) long after the computer is turned off (basically forever).  The data would have to be extremely important to even try that method, though (due to expense and the sheer number of "if's").  But, strictly speaking, both of those are actually examples of poor implementation.
The AES standard can be broken in thirty seconds with **direct access**. Network access is the major limiting factor.

---

### Post by Habeouscorpus on 2011-02-12
> **techunit said:**
> The AES standard can be broken in thirty seconds with **direct access**. Network access is the major limiting factor.

What? Wtf, mate. If my memory serves me correctly, the AES standard is supposed to be uncrackable. It's what Assange used for his "insurance file" right?

OP; Have you considered just running BleachBit 3 times sequentially?

---

### Post by techunit on 2011-02-12
twelve years ago that may have been true. If you do a few google searches you will find something along those lines. It is very far from being uncrackable. I was incorrect in saying 30 seconds it was 65 milliseconds in order to obtain the key. That isn't actually breaking the encryption but it isn't impossible

---

### Post by JuicyCouture on 2011-02-12
sooo sfill or bleachbit

got it

---

### Post by Nixarter on 2011-02-14
[techunit]("http://ubuntuforums.org/member.php?u=1045873")...

that's only if the system is on, and the keys are in RAM (like I mentioned earlier).  Direct access to the drive changes nothing.  Of course it can be accessed if already decrypted... but that doesn't really bring anything to the table.

If properly implemented, aes encryption will keep your data safe.  period.  direct access or not.

---

### Post by dargaud on 2011-02-14
So much bul$hit in this thread...
> Whether you run 1 pass, or ten thousand passes, If I'm determined enough, I will recover data
Nope, nobody has ever proven that it's possible to recover data beyond one pass. Yeah, electron microscope yada yada, I've heard that one and it's bulsh1t. So "dd if=/dev/zero of=toto bs=1M; rm toto" will wipe the free space on your drive alright.
> Your going to need to have had your data encryped with at least three layers of high-end algorithms, a dedicated bootloader and at least a 128 charactor password
More BS. There's actually ample evidence that using layers of encryption is not only useless but actually counter-productive (it makes the key easier to find). Althoug he's got a point: it's better to encrypt your data than to delete it ! And if somebody really wants your data, encrypted or not, they'll put a hardware keylogger on you keyboard cable. Done. When was the last time you checked your keyboard cable ?

---

### Post by Lokiii on 2011-02-25
> **techunit said:**
> twelve years ago that may have been true. If you do a few google searches you will find something along those lines. It is very far from being uncrackable. I was incorrect in saying 30 seconds it was 65 milliseconds in order to obtain the key. That isn't actually breaking the encryption but it isn't impossible

AES itself cannot be cracked as there are no known vulnerabilities for it. However, you can brute force it, but the time that will take depends on the key. A lengthy password with a decent amount of ComP1exity! will take so long, even the specialized $10,000,000 super computers you can buy will struggle for a long time.

---

