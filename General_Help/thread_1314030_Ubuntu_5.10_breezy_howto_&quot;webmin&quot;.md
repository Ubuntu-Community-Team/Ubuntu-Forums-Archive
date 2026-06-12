---
title: "Ubuntu 5.10 breezy: howto &quot;webmin&quot;?"
date: 2009-11-04
forum: General Help
---

### Post by fifoKamb3 on 2009-11-04
Hi,
What is required to install/use webmin?
Thanks

---

### Post by CharlesA on 2009-11-04
Should be the same as everything else. Download the deb from webmin.com

I don't know if there is still support for 5.10 tho, since it's already EOL.

---

### Post by HiImTye on 2009-11-04
there is no support for 5.10. even if it was an LTS

---

### Post by t0p on 2009-11-04
Don't use Breezy: it's no longer supported, meaning no updates.  If you're going to take it online (as your question about webmin implies), there may be (in)security issues.  It uses *very* old versions of software.  When it was new, it was good.  But now... it's not.

Download a newer version of Ubuntu: Hardy might be a good option, as you might like to use eBox rather than webmin, and the [documentation]("https://help.ubuntu.com/community/eBox") I found on using eBox with Ubuntu all seems to refer to Hardy.  

As for webmin: there are instructions [here]("https://help.ubuntu.com/community/WebMin") on how to use it with newer versions of Ubuntu.  But it was dropped from Ubuntu because it is not compatible with the way that Ubuntu packages handle configuration files, and it can cause unexpected problems. As I mentioned above, an alternative web-based admin tool is eBox.  You'll find some info on how to use eBox with Ubuntu [here]("https://help.ubuntu.com/community/eBox").  Though the documentation does look a little patchy.

---

### Post by Soul-Sing on 2009-11-04
I thought webmin was dropped out the off. ubuntu repos.2 years ago, because there were security issue's.

---

### Post by fifoKamb3 on 2009-11-04
Thanks 4 ur replies.

I am bittorrenting Ubuntu server 9.10.

Is perl by default available in 9.10?

LTS? EOL? Take it easy my friends! :)

Br,

---

### Post by P4man on 2009-11-04
> **fifoKamb3 said:**
> Thanks 4 ur replies.

I am bittorrenting Ubuntu server 9.10.

Is perl by default available in 9.10?

LTS? EOL? Take it easy my friends! :)

Br,

EOL= End Of Line.. 
LTS= Long Term Support. A very stable release that is supported for 5? years. You might actually want to download the latest LTS (ubuntu 8.04) instead of the somewhat more experimental 9.10, depending what your needs are. For a server Id go 8.04 for sure. For a desktop or workstation you could give 9.10 a try.

And yes perl is included.

---

### Post by t0p on 2009-11-04
> **P4man said:**
>  You might actually want to download the latest LTS (ubuntu 8.04) instead of the somewhat more experimental 9.10, depending what your needs are..

I agree with your suggestion that the OP might prefer to use 8.04 (Hardy Heron).  But it isn't accurate to call 9.10 "experimental".  Karmic is (allegedly) stable.

---

### Post by P4man on 2009-11-04
> **t0p said:**
> I agree with your suggestion that the OP might prefer to use 8.04 (Hardy Heron).  But it isn't accurate to call 9.10 "experimental".  Karmic is (allegedly) stable.

I called it *somewhat more experimental*, I think thats a fair statement when comparing it with hardy :) Sure its a stable release, but more likely to give headaches than hardy, and if the OP was still using breezer, I think he'll be more than happy with hardy and its features without craving all the new features of karmic.

---

### Post by HiImTye on 2009-11-04
> **t0p said:**
> I agree with your suggestion that the OP might prefer to use 8.04 (Hardy Heron).  But it isn't accurate to call 9.10 "experimental".  Karmic is (allegedly) stable.
all versions of ubuntu are 'experimental' as they generally use the debian\experimental branches (all of them to my knowledge)
generally the LTS are LTS because they are more stable initially (or so I have seen) and they tend to get better/more stability

---

### Post by fifoKamb3 on 2009-11-04
> **P4man said:**
> , depending what your needs are.
Learnling Linux, that is all.
Thank u.
I downloaded 9.10 and I try to install it, I faced the first problem* (I have to download 32-bit), but I opened another [topic]("http://ubuntuforums.org/showthread.php?p=8240482#post8240482") to know more about that.

___________
* (This kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - please user a kernel appropriate for your CPU.)

---

### Post by fifoKamb3 on 2009-11-04
And so far installed but:
> -bash: wget: command not found

Why is that?

---

### Post by Slim Odds on 2009-11-04
> **fifoKamb3 said:**
> And so far installed but:


Why is that?

Looks like wget is not installed?

Try:```
sudo apt-get install wget
```

---

### Post by t0p on 2009-11-04
> **Slim Odds said:**
> Looks like wget is not installed?

Try:```
sudo apt-get install wget
```

Wget not installed?!!  But that's... ridiculous!!  Can someone who's running Karmic please confirm, is wget not installed by default?

If not, that is just stoopid!  That's 2 everyday *nix utilities that seem to have been dropped by Ubuntu (both beginning with "w" - is there a pattern? :p): **wget** and **wvdial**.  Why are these programs being dropped?  They're very small, so it isn't like the devs need the extra space.  And okay, maybe some folk think wvdial isn't needed (though it would be very arrogant - plenty of people still depend on ppp)... but wget certainly *is* a utility that many users need on a daily basis!

Wget dropped from Karmic?  Someone please tell me it ain't so!

---

### Post by P4man on 2009-11-04
> **t0p said:**
> Wget not installed?!!
Wget dropped from Karmic?  Someone please tell me it ain't so!

It aint so.

---

### Post by coffeecat on 2009-11-04
> **t0p said:**
> Wget dropped from Karmic?  Someone please tell me it ain't so!

Relax! :) I downloaded the Kubuntu Karmic ISO in Ubuntu Karmic using wget.

---

### Post by t0p on 2009-11-04
> **P4man said:**
> It aint so.


> **coffeecat said:**
> Relax! :) I downloaded the Kubuntu Karmic ISO in Ubuntu Karmic using wget.

Ah, good.  Thank you P4man and coffeecat.

OP: that error message is strange, considering that wget *is* installed in 9.10.  Could you post the entire command that provoked the output "-bash: wget: command not found"?

---

### Post by P4man on 2009-11-04
> **t0p said:**
> Ah, good.  Thank you P4man and coffeecat.

OP: that error message is strange, considering that wget *is* installed in 9.10.  Could you post the entire command that provoked the output "-bash: wget: command not found"?

sounds like he entered that command in windows CLI. in ubuntu (bash) the exact phrase is *"No command xxx found"* (usually followed by a helpfull *"did you mean xxy"*. *Command not found *I think is windows speak. Im wondering if the OP thinks linux is a windows program that he installed and wants to run from the CLI....

---

### Post by fifoKamb3 on 2009-11-05
Thank you all
P4man: no,
I installed it and run it virtually on Ubuntu Desktop 9.10. Today I decided to do the installation again, because I did not understand all  steps I took :)

Let's say > **partitioning method:**
Guided - use entire disk
Guided - use entire disk and set up LVM
Guided - use entire disk and set up encypted LVM
Manually:
Guided partitioning
Configure iSCSI volumes

iSCSI (0,0,0) (sda) - 17.2 GB ATA Virtual HD

Undo changes to partitions
Finish partitioning and write changes to disk



---

