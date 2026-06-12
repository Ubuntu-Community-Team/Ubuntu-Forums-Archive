---
title: "E: Could not perform immediate configuration on 'util-linux'.Please see man 5 apt"
date: 2010-05-15
forum: General Help
---

### Post by copperhead27 on 2010-05-15
I ran into this problem myself, and I've seen that others have had the same problem when updating from Karmic to Lucid via apt-get. There is a bug in apt for Lucid, and it has been noted on one of the Ubuntu lists (sorry, I lost the link.)

This is a simple how-to and a work-around to the upgrading with apt-get:

1) Update your sources.list file to replace all instances of 'karmic" to 'lucid' :

     $ sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list

2) Run apt-get update:
   
     $ sudo apt-get update 

3) Run a regular upgrade;

     $ sudo apt-get upgrade -y

Here is where the problem comes in. Apt is looking for the util-linux package, which is part of upstart-job, but someone apparenlty forgot to write the code to tell apt-about this (whoops!) 

So, you now need to install upstart-job by itself. By skipping this step you will get the error message when you try to run step 5: "**E: Could not perform immediate configuration on  'util-linux'.Please see man 5 apt" **

4)   $ sudo apt-get install upstart-job

5) Now you can run apt-get dist-upgrade:
  
      $ sudo apt-get dist-upgrade -y

Hope this helps out anyone who got stuck.

---

### Post by radsdau on 2010-05-23
Helped me out- many thanks! 
I just wonder how you found out what the problem was and then how to solve it.  More clever than me I guess!!!
radsdau

---

### Post by luigie on 2010-06-05
Thank you [copperhead27]("http://swiss.ubuntuforums.org/member.php?u=1075489").  My problem was resolved.  :)

---

### Post by JoseRijo on 2010-06-07
Interesting.  I was using aptitude to upgrade.  Instead of upstart-job, I had to do:

$ sudo aptitude install upstart

But that worked great.  Thanks for the lead!

---

### Post by estraven on 2010-07-01
& thanks from me

---

### Post by Neal2 on 2010-09-05
Thank you very much for this.  For the record, the aptitude command should be:

sudo aptitude install upstart

Neal

---

### Post by oguillaume on 2010-11-01
Thanks, that did the trick.
... followed by sudo apt-get dist-upgrade

---

### Post by mastmaulaa on 2011-10-06
thanks a ton

---

### Post by oldos2er on 2011-10-07
Closed, necromancy.

---

