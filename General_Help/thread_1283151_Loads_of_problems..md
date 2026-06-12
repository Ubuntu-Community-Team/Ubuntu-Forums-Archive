---
title: "Loads of problems."
date: 2009-10-05
forum: General Help
---

### Post by Eric_D on 2009-10-05
Hi all, sorry this may be a long post.

I have been using Ubuntu on 2 computers for about 6 months now and in the beginning everything seemed ok, apart from YouTube video problems on my "server". Since about 6-8 weeks I have started getting a lot of problems with my laptop as well, which is my main computer that I use.

Laptop problems running latest version of Ubuntu.

1) Skype sound does not work any longer, that is, it sort of works but have a long delay between me speaking and the oerson I am speaking with hears me. He says the sound also sounds like a robot, very quiet and crackly.

2) At the beginning I was using Evolution and it worked perfect but then I started getting error messages, can't log in to check my emails. Shortly after that the error messages stopped but it would not download any emails, new or old.  Now it works intermittently,sometimes I get error messages that it can't log in and other times it just does not download my messages but sometimes it does.

3) When I started having the above probs with Evolutuion I installed KMail, it worked ok for about a week but now I am getting the same intermittent probelms as Evolution. 

4) VirtualBox never worked and still can't get it to work.

5) Never got Wine to work.

6) Sharing just stopped working, can't even print.


PC problems running Ubuntu Server. 

1) Youtube sound worked at the beginning but had Video problems. 2 Days ago I tried it again and it wanted to search for and install some codecs. After it found and installed them I now only get sound but no video at all, only get a blank white video. 

PS: On my Laptop, Ubuntu never asked me about these codecs, don't know if it installed them wiothout my knowledge.

2) Skype problems the same as my Laptop. 

3)  Evolution the same as my Laptop.

4) About 2 weeks ago I got a red X on the network icon, it tells me that the net card is not "managed". When I click on "Connection Information" I get a "Error displaying connection information: No valid connection information found" message BUT I am able to connect to the internet and surf.

5) Wine never worked.

6) VirtualBox worked at the beginning but no longer works. 

7) On bootup I get a "comspec failed- (error= -16)", it stays there for w few seconds and boots normally. 

8) During bootup, I also get a "kvm" failed error message. 


I tried Kubuntu on both computers but had more problems than with Ubuntu. 

My two computer specs.

Laptop: Advent 7099, Intel Core Duo T2300 1.66GHz with 2gig Ram. Running Ubuntu

PC: Dell Dimension 8400, 3.02GHz, 1gig RAM. Running Ubuntu Server. 

All updates on both computers up to date. 

Any help greatly apreciated.

Thanks

---

### Post by sedawk on 2009-10-05
Are both computers using the same internet connection?

On both computers you can run "dmesg" to see latest messages
in kernel buffer. Any "link up/down" cycles there while
you see the errors?

About wine. Try this:
```

mkdir /home/<user>/wine_newtest
export WINE_PREFIX=/home/<user>/wine_newtest
wine winecfg
wine winefile

```
Does the wine configuration dialog start?
(Exit with "okay" or whatever button there is ...)
Does the wine tool winefile start properly (replacement
for the explorer) or what error messages are there?

---

### Post by jkysam on 2009-10-05
A couple of recommendations:

You may wanna break up this thread. There are Ubuntu forums dedicated to help people with Virtualization, Wine, networking etc... If you post your problem with the error faulty behavior that you are seeing, you will get good help from the people that monitor those forums.

On another note, it seems that a lot of your problems boil down to network related issues. Do you have wireless configured for these machines? Try disabling it if you do. Even after configuring and installing the driver for my wireless adapter it was causing all sort of strange problems. Eventually I just disabled it...

---

### Post by Iowan on 2009-10-05
> **Eric_D said:**
> 4) About 2 weeks ago I got a red X on the network icon, it tells me that the net card is not "managed". When I click on "Connection Information" I get a "Error displaying connection information: No valid connection information found" message BUT I am able to connect to the internet and surf.
 Network Manager generally will not manage any interface configured in */etc/network/interfaces*. Ordinarily, that file should have only two lines - configuring the loopback device ("lo").

---

### Post by Eric_D on 2009-10-05
Thanks for the replies all,

Have done a lot of research today trying to find out what was wrong and found out my main problem, most of it, at least on the email and skype, has to do with the updates of some sort, donno exactly what yet.

Sometime ago I did a "live CD" backup of my Ubuntu installation using Remastersys, I booted up to this CD and emails and skype work on there without any probs. I have kernel 2.6.28-11 on there which was the version I installed before making the "live CD".

On my Laptop I have kernel 2.6.28-11 and 2.6.24-23, emails and skype sound do  not work on either version so I can only guess that the updates somehow messed up a few things. I'll reinstall from the live CD but will not update initially to see what happens. I'll do the updates again in a few days to see if anything is going to stop working. 

I have no wireless card on the "server" where I have the red X. 

There is no entry in the Laptop cmos to disable the wireless.

Both computers use the same internet connection and I have no problems surfing the internet, just skype sound and youtube video problems on the "server", no problems with youtube or any other website videos on the laptop but Skype sound and Evolution/KMail have stopped working. 

I will try your Wine suggestions and post any error messages I might get.

/etc/network/interfaces does only have two lines in it.

auto lo
iface lo inet loopback

Thanks for all your help, really appreciate it.

---

### Post by Eric_D on 2009-10-06
Just to update this thread which some might find useful.

I down loaded OpenSolaris and installed it on my Laptop, same problems with Evolution here as well but funny enough Thunderbird does work.  

I have not been able to install Skype or Flash because I don't know how to in Solaris, don't even know how to log in as root to copy the necessary files in to the right folders. 

I'm going to reinstall Ubuntu and give Thunderbird a go, hopefully it'll save me having to go back to Windows which I really don't want.

---

