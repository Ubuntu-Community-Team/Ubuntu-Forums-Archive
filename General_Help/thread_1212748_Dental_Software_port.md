---
title: "Dental Software port"
date: 2009-07-14
forum: General Help
---

### Post by dajomu on 2009-07-14
I came across a open source dental software or a so called "Open Source Practice Management" that would have been great to make available to ubuntu users. Could be a great way to get Linux into dental-offices. No cavity with Linux :)
Anyone up for the task? I do not have the skills to do that so...

Forgot to add a link to the software.... It is called Open-dent and found [here]("http://open-dent.com/")

---

### Post by ericab on 2009-07-14
"No cavity with Linux"

...

[IMG]http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif[/IMG]

---

### Post by easy_target on 2009-07-23
OKay, 

I had a post about this software four years ago. After a while I lost interest on the project but now I see it is more mature and actually feasible.
I downloaded the source code on the website with this command:

```
svn co https://70.90.133.65:23793/svn/opendental/opendental6.7
```

After downloading and reading the BUILDING.Linux file I picked up dependencies (mono, nant, build-essential, etc) and proceeded to use the make command.

I got an error that said something like "opendental5_6.sln not found". I edited the Makefile to match the existing .sln file in opendental directory. After that the compilation went through with just a couple of warnings. From there on I have no idea on how to use, test, or even start opendental. Anyone willing to give us a helping hand?

Thanks!

---

### Post by easy_target on 2009-07-25
Anyone out there?

---

### Post by lisati on 2009-07-25
> **easy_target said:**
> Anyone out there?

I was so busy reading the forums while eating my dinner that my fillings fell out.

....

Just kidding, but sounds like a good project (and what's left of my teeth aren't in exactly an "as new" condition)

---

### Post by mateit on 2009-09-01
Check it out here [http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/398508-opendental-6-0-svn-running-opensuse-11-0-a.html](http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/398508-opendental-6-0-svn-running-opensuse-11-0-a.html) . I REALLY am interested in getting feedback on this matter. Especially from dentists using it :-). Thanks

---

### Post by easy_target on 2010-11-04
Okay I thought that this thread would be dead by now, but since I have some more information on this, here it goes.

Solution 1 - Running OpenDental with Wine
1. add ppa repository for wine
> sudo add-apt-repository ppa:ubuntu-wine/ppa
2. Install Wine.
3. get winetricks and install dotnet20 d3dx9 gdiplus glut vcrun2008 ddr=opengl
4. wine OpenDental.exe (make sure you're in .wine/c_drive/pathtoopendental) or setup your Drives with winecfg

Solution 2 - Download Linux Compiled Executable

[http://www.onsitedentalsystems.com/opendental7.2.zip](http://www.onsitedentalsystems.com/opendental7.2.zip)
Look in OpenDental\bin\Debug folder for the compiled executable.


All work is the credit of Justin Shafer, dental linux guru. Great job Justin! If you want to know how he did it follow [this link]("http://70.90.133.65/forum/viewtopic.php?f=2&t=3057&sid=36c8e3df879bd361c8ec63fb1c71faf6")

Cheers.

---

### Post by justinshafer on 2011-01-12
Wow! I didnt thank anyone would notice! Thanks man. I am not a guru, just stubborn. It will still run on mono but you have to rip a bunch of stuff out, and its time consuming. And no 3d tooth chart with mono.

Oh yeah to get 7.5 too run you have to install the directx sdk with winetricks.. Forget the switch, but its there. Big download too.

---

