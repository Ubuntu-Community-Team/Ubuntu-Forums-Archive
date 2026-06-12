---
title: "The best Windows is XP without Internet access"
date: 2009-10-09
forum: General Help
---

### Post by UranUtan on 2009-10-09
Hi,

A lot of buzz have built up about how great Windows 7 will be. They might be true. In my case, I am not impressed. I only need Windows to run all the MS Dev & DB tools (this is my job). I have a work laptop for this. Which has Windows (which version is installed is up to company policy).

We also use a lots of VM at work and I happen to build the VMs for the team. We use VMWare ESX and for Workstation type of VM we use Virtualbox. I have created and evaluated a lot of Windows VMs (2003, 2008, 7 in x32 and x64) these VMs are dev machines using various MS Dev tools.

My home computer is Ubuntu 9.04 x64. And this is the point of this post. Which Windows version I should use at home?

I need Windows for running a few stuffs that Wine cannot do well: Visual Studio 2008 and SQL Server 2008. For other people that could be Office 2007 or Photoshop.

Here is my opinion based on all the VMs I have "played" with so far. For DEV I use Windows 2003 and for home applications I use WinXP.  These Windows are VMs (Virtualbox) **and I configured them so that they can only access the local LAN and ZERO access to the Internet**. To block Internet access I use a double precaution:

1. Configure the Windows TCP/IP Properties so that the default Gateway is empty.

2. Configure the router to block Internet access to these Windows VM by their MAC address.

I know it's redundant but either one can be accidentally changed and invalidate the blockage.

As a result, these Windows VM doesn't need Antivirus, AutoUpdate. Never need to open a browser. When file exchange is needed, I use Virtualbox shared folder. In my case, these VMs run perfectly the few applications I need. The VM boot very fast and they require very few maintenance (no more craps and bloat to clean up). In particular, they are unattackable.

Of course, I have tried Win7. Besides the activation headache (when the host machine changes the activation status is reset), the new cool features cannot compensate for the slower boot time and much higher resource consumption. And I don't use any of these Win7 cool stuffs as 99% of the time I open the DEV application. As the VM is isolated from the Internet, the security argument of Win7 is irrelevant.

In conclusion, for me the best combination for home use is: using Linux as the main OS. For running Windows applications (that Wine cannot handle), use a Virtualbox VM with WinXP as guest OS _AND_ block Internet access of this Windows VM. Not sure if that will fit everybody's scenarios but at least this works well for me.

---

### Post by Boondoklife on 2009-10-09
I personally use xp in the client also, have to keep it around in my case for the crazy little apps my college classes want me to run. The others as you mentioned just bloat the install and give you pretty effects that just are not needed if you are using ubuntu as your main os.

---

### Post by UranUtan on 2009-10-10
> **Boondoklife said:**
> I personally use xp in the client also, have to keep it around in my case for the crazy little apps my college classes want me to run. The others as you mentioned just bloat the install and give you pretty effects that just are not needed if you are using ubuntu as your main os.

FYI, a VM containing Win7 or Windows 2008 is double the size of the one using Win2003. And they tend to get bloat easily when you install updates. Worst yet, they boot from 1.5 to 2x slower. 

Your college is cool. A month ago I helped a student to buy a laptop. Then after reviewing the shortlist she told me "but they are not Mac, the college wants her to buy a Mac". Is it true that a college can force a student to use a specific hardware / OS ? Do you have any trouble with the college policy b/c your laptop has Ubuntu?

---

### Post by Boondoklife on 2009-10-10
The whole forcing the hardware/os is a reality as some software just cant be run well natively in others. A great example is I have to use some SAMS website and I tried getting it working with firefox but in the end I have to use IE for some activeX controls. Long story short it was just easier for me to use a vm to run xp and then use ie in that. I have also had some classes when it was a dll nightmare with the software they wanted us to run so in that case the vm came in handy too.

The sad reality that I have come to see is that most of the college staff are over worked or simply lacking and dont look into other options well enough. They should be able to provide non-OS specific software to do exercises especially if the class is not a WINDOWS XXXX class. A perfect solution would be to use Java as the application coding of choice, but I wont hold my breath.

---

