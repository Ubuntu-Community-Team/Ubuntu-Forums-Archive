---
title: "Skype Help Please!"
date: 2009-07-10
forum: General Help
---

### Post by BrynRae on 2009-07-10
[CENTER]Hi, I'm fairly new to Ubuntu 9.04 and I'm really needing help with Skype. It's the only thing I've come across that's giving me issues! I've gone through countless forums and have uninstalled pulse and it just made things go silent. I really need help and would appreciate anything!

Before I uninstalled pulseaudio I at least had sound and mild fuzziness in the mic, but now I have nothing. So I tried reinstalling pulseaudio and nothing happend. 
 Please oh please help me.


:KSThanks:KS
     Bryanne
[/CENTER]

---

### Post by zahidraf on 2009-07-10
Did you try to find the sky for linux version if not then ..window is best :)

---

### Post by BrynRae on 2009-07-10
[CENTER]I downloaded the Linux Skype. But should I try to download the windows version and run it through wine?

:KSBryanne:KS
[/CENTER]

---

### Post by kelvin spratt on 2009-07-10
I use skype for Linux with no problems at all very good for calls from the UK to Peru crystal clear.

---

### Post by BrynRae on 2009-07-10
[CENTER]Well I have sound coming through my headset now but no playback on my mic when making test calls. Help?

:KSBryanne:KS
[/CENTER]

---

### Post by Bucky Ball on 2009-07-10
Install the medibuntu repo into your software sources then you can just select it from Synaptics, easy peasy. Bottom of this page should work but there are many how tos for all versions of Ubuntu:

[http://ubuntulandforever.blogspot.com/2008/05/medibuntu-repository-for-hardy-heron.html]("http://www.medibuntu.org/repository.php")

Don't forget to add the key, it is on that page.

---

### Post by BrynRae on 2009-07-10
[CENTER]*t**hen you can just select it from Synaptics, easy peasy.*

*I'm not sure I understand..*

:KSBryanne:KS
[/CENTER]

---

### Post by rabdoel on 2009-07-10
hi what bucky ball means is to add the mediabuntu repository using this instructions on this link - [http://ubuntulandforever.blogspot.com/2008/05/medibuntu-repository-for-hardy-heron.html]("http://www.medibuntu.org/repository.php")

and then from the menu bar on the top select system>administration > synaptics package manager . then search for skype and install it

---

### Post by Bucky Ball on 2009-07-10
Okay. How to add the Medibuntu repository to your sources list in 9.04, taken from [this]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories") page. 

* Take Note: Ignore my previous link. It is for 8.04 and I notice you are talking about 9.04

Go to:

Applications->Accessories->Terminal.

Copy this command into the terminal:

   ```

sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list

```Copy this one to add the GPG Key:  

```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```Now, go to:

**System->Administration->Synaptic Package Manager**

Click it. In the toolbar along the top you will see a** 'Search'** option. Search **for 'Skype'**.

When you find it, click the box to the left of it and **'Mark for Installation'**

In the same toolbar as search, hit** 'Apply'** to install. When finished, you should have Skype in:

**Applications->Internet (or Network)->Skype**

You can drag it out of there and plop it in your top taskbar along with other regularly used programs or on the desktop or in a folder or wherever (this creates a copy and original shortcut stays in the 'Applications' menu).

:)

---

