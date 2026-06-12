---
title: "Good Budget Nvidia card for 9.10"
date: 2009-11-24
forum: General Help
---

### Post by Quarkrad on 2009-11-24
Just installed 9.10 on a friends machine - was hoping to give him the delights of compiz and cairo dock.  Problem is - he has a Radeon 9600 graphics card which is not supported so he only has _System/Preferences/Appearence/Visual Effects  **None:**_    he cannot get  **Normal:** or **Extra:**

It seems to me Nvidia is better supported than ATI by Ubuntu - can anybody suggest a budget Nvidia graphics card that will give my friend good 3d desktop graphics.  (He is not into games or photo editing etc).

---

### Post by phidia on 2009-11-24
> **Quarkrad said:**
> Just installed 9.10 on a friends machine - was hoping to give him the delights of compiz and cairo dock.  Problem is - he has a Radeon 9600 graphics card which is not supported so he only has _System/Preferences/Appearence/Visual Effects  **None:**_    he cannot get  **Normal:** or **Extra:**

It seems to me Nvidia is better supported than ATI by Ubuntu - can anybody suggest a budget Nvidia graphics card that will give my friend good 3d desktop graphics.  (He is not into games or photo editing etc).

It's not only Ubuntu support that's lacking but you'll find most linux distros favor nvidia BUT that has been changing I'm not sure that the Radeon can't be made to work although maybe ATI itself has dropped support for the driver?

If you want to find a good replacement card then checking the bargains at newegg or tigerdirect should work. Also look at the [hardware compatibility lists]("http://ubuntuforums.org/showthread.php?t=361236&highlight=radeon+9600").

---

### Post by XCan on 2009-11-24
I would just go for one of the current-generation low-end video cards from nVidia. GT 210, for example, comes to mind. What will matter in the end is if the properiatary drivers from nvidia supports your card. This is also where AMD fails it. Their drivers suck. Unfortunately, it's hard for anyone but the companies to implement the required functions.

---

### Post by james_xxx on 2009-11-24
I have an older laptop with a Radeon Mobility M6 LY graphics card. This card worked fine under Jaunty, with compiz working smoothly. However, this card card did not work very well when I tried out an Ubuntu Karmic Live CD. After exploring various options, I put Jaunty back on the machine.

So, one option you could consider, would be installing Jaunty for your friend. It will be supported for some time yet.

Another would be looking through the forums to see if others with this card have been able to create an xorg.conf that causes the Radeon 9600 to work well.

One more possibility would be to consider a different distribution. I do have a machine with an AGP Radeon 9000, running Fedora 12. Compiz is running beautifully on that box. (I have never had Ubuntu installed on it, so I do not know how well the Radeon 9000 would work under Karmic.)

I should also add that if you do decide to switch cards, I have a PCIe Nvidia 8400 GS on my main desktop that has done really well. I bought it a year or so ago at Best Buy for less than $50.

---

### Post by Quarkrad on 2009-11-24
Thanks to all

---

