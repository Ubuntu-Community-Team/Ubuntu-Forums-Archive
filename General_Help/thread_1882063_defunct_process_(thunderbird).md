---
title: "defunct process (thunderbird)"
date: 2011-11-16
forum: General Help
---

### Post by allenb.bigal on 2011-11-16
I've been having problems with Thunderbird lately and I was wondering if anybody else had experienced the same.

facts:thunderbird 7.0.1
     :10.04 (up to date)

problem:
Whilst connected to the internet, thunderbird starts to give problems. What happens is that I cannot access anything on any of thunderbird's sub menus. This is annoying because I have to kill the process to clear it.

I have detected that there is a defunct process belonging to thunderbird. Here's the details:-

allenb@allenb-desktop:~/Desktop$ cd

allenb@allenb-desktop:~$ ps -ef|grep -i thunder

allenb    2600     1 12 07:44 ?        00:02:26 /usr/lib/thunderbird-7.0.1/thunderbird-bin

allenb    2603  2600  0 07:44 ?        00:00:00 [thunderbird-bin] <defunct>

allenb    2923  1797  0 08:04 pts/1    00:00:00 grep --color=auto -i thunder

allenb@allenb-desktop:~$ kill -9 2600 2603

allenb@allenb-desktop:~$ kill -9 2600 2603

bash: kill: (2600) - No such process

bash: kill: (2603) - No such process

allenb@allenb-desktop:~$ ps -ef|grep -i thunder

allenb    2925  1797  0 08:04 pts/1    00:00:00 grep --color=auto -i thunder

allenb@allenb-desktop:~$ 

I'm wondering if somebody is playing silly buggars with me. If I disable networking the problem doesn't occur.

Thanks

Allen

---

### Post by allenb.bigal on 2011-11-17
It appears that I was not quite correct with my initial diagnosis of this problem. Further investigation reveals that there seems to be a defunct process present all the time that thunderbird is running and is cleared when thunderbird is quit.

The rest of the initial description of the problem are current, although the problem hasn't surfaced again (yet).

Allen

---

### Post by allenb.bigal on 2011-11-18
Although there's plenty who have looked at my posts, not a soul has suggested anything. A bit disappointing.

Nevertheless I have bitten the bullet and attempted to revert to a previous version of TB. Don't know how it happened but I finshed up with TB V.8.

So it's now a waiting game to see what happens (if anything). However, I have noticed that TB doesn't spawn the process that goes pear shaped and changes the spawned process to zombie. As I have said in an earlier post, the zombie (or defunct) turned out to be a red herring and had no apparent affect on my problem.

As they say in the classics, "stay tuned to the next exciting episode"!
Allen

---

### Post by allenb.bigal on 2011-11-19
Well the TB menu access problem has re-appeared despite upgrading to TB 8!

I've changed the title to more correctly align with the problem.

I'm still thinking that somebody's getting at me. Any suggestions as to how to find out if this is the case and then what to do about it. At the moment I'm simply disabling networking which seems to stopit but when I do want to check my email I'm then vulnerable again.
This is really peeing me off!
Allen

---

### Post by Enzo65 on 2011-11-23
Hi, just observed the same. But the defunct process seems to disappear as soon as the add-ons page is opened - can you confirm that?

--enzo

---

