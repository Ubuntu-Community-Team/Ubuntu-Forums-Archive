---
title: "Adobe Flash Player"
date: 2009-07-08
forum: General Help
---

### Post by colintivy on 2009-07-08
Hi folks,

I have suspected that, although Flash Player is installed on my laptop, as indicated in Synaptic, it does not actually work. A recent letter in Linux Format 121 August 09 p19 suggests that it is necessary to install "the appropriate wrapper" before AFP will work. Does anybody know anything about it? I cannot find any likely references to one but live in hope!!

colintivy:confused:

---

### Post by oldos2er on 2009-07-08
Are you running 64-bit Hardy? If so, you would only need a "wrapper" if you want to run 32-bit Flash. If you read the stickies in the 64-bit subforum, there is a script you can download to install 64-bit Flash.

---

### Post by colintivy on 2009-07-09
Hi oldos2er,

That nom de plume dates you like me!!

No I am still on Hardy 32 bit. My old Pent111 laptop is just up to coping with that. My suspicions about AFP are that some feature and/or images do not display and I installed the current AFP from Synaptic but to no avail. This letter gave me hope that a solution was in sight. It only specified Ubuntu but no version or bits. The sub-forum was not very helpful. Do you believe that 32 bit does not need a wrapper?

colintivy still:confused:

---

### Post by oldos2er on 2009-07-09
Is the Linux Format article online? And no, 32-bit Flash needs no wrapper.

---

### Post by twright on 2009-07-09
I suggest you just install the .deb installer from Adobe's site, that works fine for me whereas I think that the package in the repos may be a little broken.

---

### Post by colintivy on 2009-07-10
Hi 0oldos2er,

Thanks for that, I will not follow the line to a wrapper. I have not looked at the Linux Format on line, the letter is in the current issue but I do not know right now if only the editorial and feature articles are all that is displayed. When I have 5mins I will have a look to see for you. It has been suggested that the Synaptic repos for AFP might be broken and it might be beneficial to use the .deb installer from Adobe itself. This would probably mean that updates would not be available as routine on the Ubuntu update manager would it not?

Bye for now,

colintivy :)

---

### Post by twright on 2009-07-12
> **colintivy said:**
> Hi 0oldos2er,

Thanks for that, I will not follow the line to a wrapper. I have not looked at the Linux Format on line, the letter is in the current issue but I do not know right now if only the editorial and feature articles are all that is displayed. When I have 5mins I will have a look to see for you. It has been suggested that the Synaptic repos for AFP might be broken and it might be beneficial to use the .deb installer from Adobe itself. This would probably mean that updates would not be available as routine on the Ubuntu update manager would it not?

Bye for now,

colintivy :)
I think that the package in the Ubuntu update manager just downloads and installs the one from the adobe site anyway. Either way it should be automatically updated just as any other package would be.

---

### Post by GCoffee on 2009-07-12
Uninstall flash via synaptic (Be sure to check Complete Removal)

Then start firefox and go to a website that has flash content on it, and firefox should ask to install addons for media on the page. Select Adobe Flash Player from the list it gives you and click next, it should install and ask you to restart firefox.

Thats what I did anyway.

---

### Post by colintivy on 2009-07-18
Hi GCoffee,

Thanks for that, I have finally got round to giving your idea a whirl but with mixed results. Perhaps you can elucidate please.

Duly removed AFP using Synaptic as suggested and the indication were as expected, then went to an undisplayed web image and then the Adobe Website. There I downloaded the .deb from their download page. This all went in OK except that during it, a pop-up it told me that I had a later version installed! On looking at Synaptic again I noted that the download installed Version was now 10.0.22.87-1 wheras Synaptic told me that the latest was 10.0.22.87-2. I duly let it instal that and looked at an image (black screen as usual). On right clicking it it referred to Adobe 9 which was a surprise!.

Why did the complete un-install not work ? All the apparent signs were as expoected and why do images still suggest Version 9? (presumably they have been around for that long).
Even so I would expect the later Version to be backward compatible. It all is very strange but even the latest Version does seem to have mucked up some other 
bits that used to more normal before this even though images are not!!!

I usually succeed in looking at images when they are attachments to emails but not if they are included within the text of the email. Some images on websites are OK but others just show black rectangles. I am using Firefox 3 with Hardy for now if that is relevant.

colintivy :(  :(

---

### Post by colintivy on 2009-07-21
Hi oldos2er!

Sorry that I mis-spelt your nom-d-p...finger trouble + inattention. I have looked at the Linux Format website, sadly it does not display the letters page but that would not help you much anyway, you also have to be registered as a subscriber to look at most of it.

I am a bit mystified because, although Synaptic shows that I have the latest Plug-in installed, there is evidence that the old 9.0.159.0 is still also installed despite what Synatice says! It seems that Firefox is using the old one which may contribute to the fact that some images will display and others do not. My reply above say it all.

colintivy  :[

---

### Post by kc4mts on 2009-07-23
Hello There!
Try this to solve your issue...It worked for 32 bit Ubuntu 8.04
One other thing you can try is as follows: (follow these directions ONLY IF you are using Ubuntu AND Synaptic Package Manager) in Synaptic search for Adobe flash and right click and chose "mark for complete removal" Adobe-flashplugin and select apply. Only after this is completed, do NOT install from Synaptic, instead, go to [http://www.adobe.com/go/getflash](http://www.adobe.com/go/getflash) and select the correct package for you system ( they have YUM, tar.gz, rpm, and deb packages... for Ubuntu that is usually the .deb package) at the time of this writing it is version 10.0.22.87-1 and I would recommend installing instead of saving and then installing( it saves a lot of work). This should get your flash pages working. Almost as soon as you finish doing this, synaptic will alert you to an update (ver 10.0.22.87-2). This update from Ubuntu repositories seems to work fine.
Back ground: I have not had flash working for a long, long time and and completely removing it and re-installing from Adobes site (not the Ubuntu repository)
seems to have cured my problems. I can only assume that something was incorrect on the 8.04 Ubuntu Live CD or one of the updates shortly after I reinstalled Ubuntu on this machine. The original Flash version was 9.0.....something.

Disclaimer......this fix may work for other flavors of Linux but has not been tested on them... use at your own risk. Back up files if possible before trying this method as I REALLY do not like screwing up other peoples machines....remember re-image takes 20 minutes and one or two explitives....reinstall can last a lifetime.

---

### Post by robbie d on 2009-07-23
Make sure all other flash versions are uninstalled also, it makes it hard when there are several different packages installed for flash.

---

### Post by colintivy on 2009-07-23
Hi robbie d,

That sounds interesting. Is there any directory or whatever where I can find out precicely what I do have installed? Synaptic only shows the latest one but it does appear from earlier posts that there is a Version 9 around. There may be others of a different origin i.e. Shockwave thaty may there.

Regards,

Colin

---

### Post by colintivy on 2009-07-23
Hi kc4mts,

Thanks for serious exposition. I will have a bash (pun not intended) when I have heard from later post. I have seen in another forum somewhere (not here) that someone on a later version of ubuntu (9.04?) has had exactly the same problem, so it is not only 8.04. 

Hope not to bother you again.

colin

---

### Post by colintivy on 2009-07-31
Hi robbie d,

By accident, I was looking for something else, I have found out why Synaptic showed only one Adobe FlashPlayer (10) installed. Much further down the list I found FlashPlayer plugin listed and it was 9 as you suggested. I have now uninstalled it and reinstalled 10 and, hopefully all will be OK. Thanks.

colintivy :)  :)

---

