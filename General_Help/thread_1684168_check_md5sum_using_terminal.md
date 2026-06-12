---
title: "check md5sum using terminal ?"
date: 2011-02-08
forum: General Help
---

### Post by holmziep on 2011-02-08
Hah!

I'm a beginning beginner here.  Downloaded Ubuntu 10.10 and want to now checksum or verify my download, but already burned a cdw on my newer Dell, then ran it live on old Gateway 5300 solo laptop, ran it live, and sorta got to the main Ubuntu after some squeek and swalks from the GW's DVD/CDR.  HAH again!  I'm hooked.

OK, someone direct me to where I can learn to open a terminal and navigate to the directory.  Hyperterminal?  DOS command line?  I am confused (as you can tell).  I want to learn that procedure as I guess it it necessary do do most things.  Have some previous edu. and experience but darn if it hasn't jelled in my brain yet so direct me to the beginner's corner.  Hah!  I'm over 50!  

Throw me some spots to read some rudimentary operational stuff about how to work terminal, perhaps recommend one, and I can run md5sum myself. 

I've been on the page above in the title bar, got there by following the Ubuntu download page, I'm just a little old, never got a decent teacher but on computer forums. 

Tks!  holmziep

---

### Post by helicase on 2011-02-08
Yep, the terminal is a bit like the DOS command line. You can find it in Applications>Accessories at the top left of your screen. Here's a link with the most important commands: [https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")
The command for the checksum is ```
md5sum -c <filename>
``` This will output the actual checksum, so you can compare it with the expected sum manually. Or, if you have a text file called 'md5sum' with the checksum in it in the same directory, you'll get an OK message if the sums match.

---

### Post by holmziep on 2011-02-13
Tks for the reply, helicase.  The following is too long, I know.  Sorry,  but I am invigorated with excitement, and I want to learn as much as  possible.

SO...**Hah!** a third time!  .  I'm movin' right along here as you will  see... But, helicase, I would of had to  Verify the check sum  above previous to my  installation of UBUNTU, Thus my confusion.  I decided to wing it...and I'M UP AND RUNNING!!

FYI,  I am a Ham (Amateur Radio) operator N2EXG, and I am motivated  substantially by my interest in the many Linux applications for the  digital and weak signal modes, many of which require only a decent sound  card.  Plus, for APRS, UBUNTU has the .AUX  subset built in (!?!)   (What ever that means, right?)  I'm working toward a mobile APRS setup  too.  We hams also use Logging software which can automatically  identify, verify and send acknowledgement to our various contacts  throughout the world...(AND... ALL THIS WITHOUT a MONTHLY FEE!  (Of  course, you have be polite, (no cussin')), and find pleasure in talking  or communicating with PEOPLE, many of whom hold interests in common with  your own.  Like Linux.  Radio.   Hmmm...)  

Recently I vacuumed  out a junked Dimension 8300 , cleaned and re-smutzed the 3 Gig processor  to heatsink with some ArticSilver.  It's amaising what people throw  out.  Dug up a pair of DMM 512 sticks that reasonably matched, and  though slower than capability, they dual mode nicely.  I'm even  hyperthreading, wow. and  using a 160 Gig SATA from a dead Dimension  510.

So with Linux in mind:  wouldn't ya know it... the other day I reached  down deep into the bowels of my hard drive junk  box and pulled out a 60 gig ATA jam packed with virusus and trojan  horses.  OVER 320 of 'em!  Bottom line is I disconnected the SATA drive,  and set this 60 gigger in the master IDE ATA spot,  adjusted the bios,  plugged in the USB stick with the UBUNTU ISO on it, tried the demo, and  all was OK, it seemed, dispite my not checking the check sum.  So I did  the install, and HERE I AM BROWSING AWAY on FIREFOX using UBUNTU!!! 

I  should be able to piece together three or four other rather capable  machines with a the parts I have, plus some discarded routers, and learn  how to put a server up and network 'em together.   

**ONE QUESTION** for anyone...

During install, UBUNTU asks if I  want to clean the target drive before the installation.  I said yes  though I had just reformated it with NTFS.  SO...What file sys does  Ubuntu  format?  I guess I can dig around, though I have read around the  net but did not get a definitive answer.  Just curious.

My future posts won't be so long winded, I promise.  Geez, I need a darn JOB!   

**LAST:   Any additional direction**  ("READING") for an absolute beginner would be welcome!  I have LINUX  JOURNAL from '09 through February '11, but much of the stuff is above  me.  I need a kick-start. 

Thanks again to helicase and the UBUNTU forum!

holmziep   N2EXG

Member ARRL  (arrl.org)

---

### Post by corncob on 2011-02-13
> **holmziep said:**
> 
**LAST:   Any additional direction**  ("READING") for an absolute beginner would be welcome!  I have LINUX  JOURNAL from '09 through February '11, but much of the stuff is above  me.  I need a kick-start. 


Go to [http://www.youtube.com](http://www.youtube.com) and search for Linux.  There's no end to the tutorials, demos, presentations, and discussions there.

---

### Post by Vaphell on 2011-02-13
NTFS is windows specific filesystem. Linux has few on its own, eg. ext2, ext3, ext4. Most likely your system uses ext4 type of partition. Linux can utilize NTFS partitions (so it's easy to set up a shared partition in dual boot environment) but they are not native to linux.

---

### Post by Habitual on 2011-02-13
```
md5sum /path/to/file 
```

---

