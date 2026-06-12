---
title: "Ubuntu Upgrade"
date: 2012-08-25
forum: General Help
---

### Post by JaxMax on 2012-08-25
Hello,
My Ubuntu OS is on a partitioned section of my HD and I just recently I ran update manager. It upgraded my system to version 12.04, I believe, and now everything is quite "wiggy". It seems to boot normally until the desktop comes on. When this happens I see only the desktop icons for a short time, no access to System or Administrator, then the screen goes to gibberish. The upgrade eliminated my previous versions of Ubuntu so I am stuck. I am on my Windows XP side of the partition and am a veritable novice with Ubuntu and Linux. Any suggestions from the learned crowd? Thanks Much, Jack...
PS. I realize this description is rather vague. Here are some pertinent facts about my computer:
[SIZE=2]Compaq Presario 061 EX325AA-ABA SR1950NX NA67
[/SIZE][SIZE=2]2.40 gigahertz AMD Athlon 64
128 kilobyte primary memory cache
512 kilobyte secondary memory cache
[/SIZE][SIZE=2]Board: ASUSTek Computer INC. NAGAMI2 2.00
Bus Clock: 199 megahertz
BIOS: Phoenix Technologies, LTD  3.11 09/19/200
[/SIZE]        [SIZE=2]NVIDIA GeForce 6150 LE [Display adapter]
COMPAQ FS7600 [Monitor] (15.7"vis, s/n CNC6211G2N, May 2006)
I can enter what is called a "Recovery Mode" choice at boot time but there I see everything loaded and I get a command prompt. I don't know what to type at this prompt. OK, Thanks in advance to all. Jack
[/SIZE]

---

### Post by JaxMax on 2012-08-29
Hello,
Here is an update. I figured my problem is either too vague or too simple for a response. I downloaded Ubuntu 12.04 and burned to a DVD. I can load this and boot from it. I can also run it live. My question is: If I am going to install it from boot, how do I know I am installing it on the correct partition? Will this DVD automatically install where my previous version of Ubuntu was installed (ext3 I believe)? There is a partition tool on the DVD but it seems to only allow me to re-size my current partitions, which I do not want to do. I would like to be sure about this before I install the 12.04-which I really like by the way. Thanks.

---

### Post by JaxMax on 2012-09-01
OK...it's been three days now and I've been running the Ubuntu live and deciding on the installation process. I did some searching through the forum and found some useful info. I decided to re-boot just for the heck of it and my system is now fine. I have no explanation for all of this and the Ubuntu community is strangely silent. I guess for now the problem, if there was one, is resolved. Peace Out folks! Jack.  
                                
                                                                      :guitar:

---

### Post by critin on 2012-09-01
> **JaxMax said:**
> OK...it's been three days now and I've been running the Ubuntu live and deciding on the installation process. I did some searching through the forum and found some useful info. I decided to re-boot just for the heck of it and my system is now fine. I have no explanation for all of this and the Ubuntu community is strangely silent. I guess for now the problem, if there was one, is resolved. Peace Out folks! Jack.  
                                
                                                                      :guitar:

Glad it's fixed and sorry for the silent treatment--I just now saw your post.  It probably slipped off the front page.

For the future possibility:

Run the live cd and open disk utility or gparted to find the linux partition and note it's number.  
Install the system and click on that same linux number to install it there.  Windows will show as nfts, leave it alone.

Click "Something Else" when asked where to install and then choose the linux partition.  Click Change and then give it the info it asks for.  ext 4 journaling,  choose" /: to install,  etc.

---

### Post by JaxMax on 2012-09-03
critin,
Hello. Thanks for the help. I will keep this info handy just in case or for future changes. I saw the "Something Else" option but I didn't get that far yet in exploring. It would be interesting to know what happened, but everything seemed to just work itself out. That is an experience I have never had regarding computers. This was quite an upgrade though, some people did some hard work. The new look is great. OK, Take care. Jack.

---

