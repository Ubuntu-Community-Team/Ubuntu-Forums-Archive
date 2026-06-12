---
title: "Virtualbox USB support and vboxusers user account access"
date: 2011-10-23
forum: General Help
---

### Post by afz12 on 2011-10-23
I've recently updated my notebook to Oneiric 11.10 from 11.04 and am quite happy with the overall improvements. However I cannot get Virtualbox to recognize USB now. Previously, other Ubuntu versions requires access to vboxusers in "user accounts" and placing a tick in the access box. However 11.10 doesn't seem to allow this. I open "user accounts" and unlock as administrator. However I cannot access any of these accounts - nothing opens up. How do I do this on Oneiric 11.10 so that I can add USB support to Virtualbox? Is there some special keystroke combination for opening the various options?

Although this issue affects USB usability on Virtualbox it seems like a 11.10 bug as its "user access" function doesn't seem to function. Thanks for any suggestions in advance.

---

### Post by howefield on 2011-10-23
Open a terminal and use the following command..

```
sudo adduser username vboxusers
```

Substitute username with the correct user name. :)

---

### Post by haqking on 2011-10-23
> **howefield said:**
> Open a terminal and use the following command..

```
sudo adduser username vboxusers
```

Substitute username with the correct user name. :)

+1

also make sure you have the extensions pack, and after adding yourself to group you will need to log out and back in

---

### Post by afz12 on 2011-10-23
Thanks haqking and howefield. As said, this is not a Virtualbox setup issue as Ubuntu doesn't open its user account. This is not part of Virtualbox of course. In any case, extension packs are installed and otherwise Virtualbox is fine. Also username and passwords are correct. The issue is that Ubuntu 11.10 doesn't open up its user accounts. Therefore I cannot add myself to "vboxusers". Also, as before, previous Ubuntu versions allowed this easily. So I ask, what is the "trick" or is this a bug awaiting a solution?

---

### Post by haqking on 2011-10-23
> **afz12 said:**
> Thanks haqking and howefield. As said, this is not a Virtualbox setup issue as Ubuntu doesn't open its user account. This is not part of Virtualbox of course. In any case, extension packs are installed and otherwise Virtualbox is fine. Also username and passwords are correct. The issue is that Ubuntu 11.10 doesn't open up its user accounts. Therefore I cannot add myself to "vboxusers". Also, as before, previous Ubuntu versions allowed this easily. So I ask, what is the "trick" or is this a bug awaiting a solution?

the commands were already given to allow you to add yourself 

```
sudo usermod -a -G vboxusers username 
```

---

### Post by howefield on 2011-10-23
> **afz12 said:**
> The issue is that Ubuntu 11.10 doesn't open up its user accounts. Therefore I cannot add myself to "vboxusers". 

The command above is the terminal method of achieving what you want given that the GUI method is unavailable to you.

It will add your user to the appropriate group. 

As to why the GUI method isn't there, I can only guess.

---

### Post by afz12 on 2011-10-23
Thanks again

I opened a terminal and entered the syntax. Ubuntu seemed to accept the command and password. I closed Virtualbox and reopened. It repeated the same error message that USB is unavailable and "refer to manual". Oneiric is a fresh install on this notebook and works fine otherwise. Also Virtualbox works fine otherwise. I have run versions from 8.04 through to 11.10 and previous to 11.10, Virtualbox has always worked fine with USB support. Also I have always been able to add myself to vboxusers. Therefore it seems that 11.10 is at issue here. The graphical UI for user accounts seems dysfunctional. Also the terminal approach seems to fail. Perhaps I should ignore USB support in this version. Interestingly, Virtualbox has no issues recognizing SD cards, effectively bypassing USB connectivity. Perhaps Virtualbox should simply incorporate USB support as standard and therefore avoid unnecessary hassles. Given the ubiquity of USB devices, this would seem logical. Apart from this, Virtualbox is excellent, and I like Oneiric 11.10. However, USB support seems to be one of those things that have not been well addressed by both in an integrated fashion and implemented automatically as standard between both camps.

Anyway, rather that following "should work" <=> probably doesn't work, perhaps someone who has experienced the exact same issue could reply with their solution, tested on their machine. Otherwise, it may be inefficient to pursue attempts based on supposed correct software behavior, especially given that all software has peculiarities somewhere in its function.

---

### Post by howefield on 2011-10-23
One needs a reboot for the option to take effect, apologies for not mentioning that in the previous posts. (A logout/login might work - but I'd simply reboot).

---

### Post by afz12 on 2011-10-23
Thank you howefield for your patience. I rebooted the notebook and plugged a USB memory stick in. Ubuntu recognized it of course. I ran Virtualbox and tested 2 virtual machines. Each generated the same error message

 p, li { white-space: pre-wrap; }     Result Code: 
  NS_ERROR_FAILURE (0x00004005)
   Component: 
  Host
   Interface: 
  IHost {dab4a2b8-c735-4f08-94fc-9bec84182e2f}
   Callee: 
  IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}
When running, the USB option was ghosted, corroborating an absence of USB support. So now I left wondering - is this an Oneiric 11.10 bug or a Virtualbox bug? (VB is latest version with extension pack). The terminal syntax "appeared" to work without any error message. Rebooting the notebook didn't activate USB support. Perhaps 11.10 did accept the terminal syntax, perhaps Virtualbox has a USB support bug? It may be impossible to tell which - in any case, if Virtualbox simply included USB support as an integrated standard component, there would never be any issues with USB. After all, folder support works "out of the box" without any problematic OS preliminary setup. I think I'll either wait for some new release as the months go by and perhaps the issue will resolve. Alternatively, someone might post a tested solution. In the meantime I can live without USB support in a VM. Interestingly, Virtualbox USB support works fine on another notebook running Windows 7. This doesn't require any special OS setup. Given this, and the fact that previous Ubuntu releases from 8.04 through to 11.04 have worked re USB support on Virtualbox, I tend to think that this is an Ubuntu 11.10 bug. In support of this conjecture, the "user account" GUI is dysfunctional. Further, your terminal syntax approach appeared to accept the input syntax but failed to action the command. In summary, thanks for your advice howefield but I suspect that any prospective solution may be a long time coming!

---

### Post by haqking on 2011-10-23
> **afz12 said:**
> Thank you howefield for your patience. I rebooted the notebook and plugged a USB memory stick in. Ubuntu recognized it of course. I ran Virtualbox and tested 2 virtual machines. Each generated the same error message

 p, li { white-space: pre-wrap; }     Result Code: 
  NS_ERROR_FAILURE (0x00004005)
   Component: 
  Host
   Interface: 
  IHost {dab4a2b8-c735-4f08-94fc-9bec84182e2f}
   Callee: 
  IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}
When running, the USB option was ghosted, corroborating an absence of USB support. So now I left wondering - is this an Oneiric 11.10 bug or a Virtualbox bug? (VB is latest version with extension pack). The terminal syntax "appeared" to work without any error message. Rebooting the notebook didn't activate USB support. Perhaps 11.10 did accept the terminal syntax, perhaps Virtualbox has a USB support bug? It may be impossible to tell which - in any case, if Virtualbox simply included USB support as an integrated standard component, there would never be any issues with USB. After all, folder support works "out of the box" without any problematic OS preliminary setup. I think I'll either wait for some new release as the months go by and perhaps the issue will resolve. Alternatively, someone might post a tested solution. In the meantime I can live without USB support in a VM. Interestingly, Virtualbox USB support works fine on another notebook running Windows 7. This doesn't require any special OS setup. Given this, and the fact that previous Ubuntu releases from 8.04 through to 11.04 have worked re USB support on Virtualbox, I tend to think that this is an Ubuntu 11.10 bug. In support of this conjecture, the "user account" GUI is dysfunctional. Further, your terminal syntax approach appeared to accept the input syntax but failed to action the command. In summary, thanks for your advice howefield but I suspect that any prospective solution may be a long time coming!

as for bugs I have used VBox on 11.10 and with USB support just fine.

it only failed to action the command if you are not in the group ?

---

### Post by afz12 on 2011-10-23
Thanks howefield. That this worked on another machine does not help it work on mine! Perhaps there is a 3rd variable now :) This notebook is an Acer 5920 with 4 GB ram. I have all Ubuntu updates installed. Perhaps 11.10 installs are inconsistent or machine dependent. In any case, I'm still curious why the Ubuntu 11.10  user group GUI doesn't open. I suspect that if this issue had resolution then Virtualbox USB support would be fine. I unlock "User Accounts" and my password is accepted fine. On the left panel "My Account" is visible with my name, picture and a "tick" for "Administrator". However this panel doesn't respond further. It should open with a list of functions to subscribe to but it doesn't. I click on it and it just stays as a panel. It seems therefore that this issue is still an Ubuntu 11.10 one, perhaps combined with an Acer 5920 or the specific 11.10 install I used. I downloaded this distribution last week from the official site. It installed properly without issues. However perhaps different minor releases differ in some respect - there is no way to tell. I suspect this issue is unresolvable and perhaps immaterial. Thanks for your suggestions howefield but perhaps some problems are devoid of solution. I don't relish downloading a new Ubuntu version and re-installing. This Acer 5920 is about 5 years old now and in notebook terms is geriatric. I quite like Windows 7  on a more recent notebook - this allows all 4 cores to be exposed to the virtual machine whilst this notebook has 2 cores but can only expose 1. It is best used, I think, as an alternative and possibly devoted primarily to Ubuntu applications. Again, this USB issue may well be machine specific - I have suspicions regarding this as my other notebook also has no USB issues running Windows 7 and Virtualbox (VMs for XP and Ubuntu)

---

### Post by howefield on 2011-10-23
> **afz12 said:**
> I tend to think that this is an Ubuntu 11.10 bug.

There are other possibilities, but I'll leave that for the moment lest you feel put out.

I setup VirtualBox today in an Ubuntu 11.10 host to create a Windows and Ocelot guest following these steps..

1. Install virtualbox deb package from the VirtualBox website.
2. Add user using the terminal command and reboot.
3. Install extension pack.
4. Install guest system.
5. Power down and create filter for USB peripheral.
6. Reboot and use USB peripheral.

I'm assuming as a long time Virtualbox user, you remembered to create the filter ?

---

### Post by tlcstat on 2011-10-24
Greetings,
Open a terminal and type "sudo virtualbox" without the quotes. Click on add and browse to your virtual machine and click enter. Click settings and enable USB. You can now open the VM and have USB. Until Oracle get this fixed for 11.10 you will have to open the VM as root. It is a Oracle problem and they will fix it with an update. 
This same problem occurred with the release of Natty.
tlcstat

---

### Post by mohave on 2011-10-29
Thanks for the workaround. The USB didn't work to me as root. However when I went back to use virtualbox with my user I had to re-own all the virtualVM files to my user ... and then USB worked!

---

### Post by insanity werks on 2011-10-30
I have been trying to get usb access on virtual box and when i type in the code it ask for password and i give it and poof its done but when i go check to see if I'm listed using cat/etc/groups it said file not found further more directions on setting this up are very unclear total noob to this and want to learn it any help would be great sorry if this is posted in wrong spot oh i'm using ubuntu 11.10 gnome 3 desktop and the newest virtual box

---

