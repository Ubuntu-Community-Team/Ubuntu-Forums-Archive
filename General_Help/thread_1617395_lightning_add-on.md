---
title: "lightning add-on"
date: 2010-11-09
forum: General Help
---

### Post by Bluebearbevis on 2010-11-09
Good Morning All,

Can anyone tell me if there is a version of "lightning" that is compatible with both "thunderbird 3.1.6" and "firefox 3.6.12"?  Every version I've tried is either incompatible with one or the other and won't install...

Thank you,

Richard

---

### Post by Crusty Old Fart on 2010-11-10
Yes. I'm running the same versions of Tbird and Ffox as you are.
The version of Lightning that you need is: 1.0b2
The file is named: lightning-1.0b2-tb-linux.xpi
You can get it here: [https://addons.mozilla.org/en-US/thunderbird/addon/2313/](https://addons.mozilla.org/en-US/thunderbird/addon/2313/)

---

### Post by cottfcfan on 2010-11-10
Are you using 64bit or 32bit?
If 32bit just go to add-ons in Thunderbird and install from there it works fine.

---

### Post by Bluebearbevis on 2010-11-10
Thanks for replying my FOSSy friends,

Now we get down to it:  "Incompatible Extension, "Lighting" could not be installed because it is not compatible with your Thunderbird build type (Linux_x86_64-gcc3).  Please contact the author of this item about the problem."  Lacking the skill/knowledge to create a lightning for 64 bit Thunderbird myself, do you know if one exists?

Thanks again,

Richard

P.S. Went to this site: [http://www.mozilla.org/projects/calendar/releases/lightning1.0b2.html#linux-x86-64-builds](http://www.mozilla.org/projects/calendar/releases/lightning1.0b2.html#linux-x86-64-builds)  Although it should work with my Thunderbird, this version of lightning is Not compatible with Firefox 3.6.12.  Should I care?  It's a Thunderbird add-on after all. Is there a way around the Firefox issue?

---

### Post by Crusty Old Fart on 2010-11-10
What a mess...

Found this on: [Mozillazine]("http://kb.mozillazine.org/index.php?title=Thunderbird_3.0_installation_issues&printable=yes&printable=yes#64-bit_build_specific")
> 
**64-bit build specific**

  If you use a 64-bit Thunderbird build you can't use the Mozilla  build of Lightning with it. The Calendar project only provides 32-bit  builds. Get a 64-bit Lightning build from wherever you got that  Thunderbird build. This problem typically occurs if you use a 64-bit  Linux distro that provides a 3rd party build of Thunderbird in their  repository.
So...Who knows?

The incompatibility that you experienced when Lightning complained about your version of Firefox seems really jacked to me. Maybe the code cats who were writing 64bit version of Lightning were snorting nutdust at the same time.

---

### Post by hcs7dap on 2010-11-14
I have the same issue... can't install the add-on because of incompatibility with FF3.6.12... any hints/tips welcome

---

### Post by lesannkel on 2010-11-15
I had this same problem.  So I uninstalled the previous version of lightning.  Then, instead of allowing the redirection to firefox, I found the lightning 1.02b through the Get add-ons tab of the add-ons.  Under the "recommended" heading, lightning 1.02b is listed.  Click on that and it should install in that window instead of opening firefox.  Everything works for me now.  Hope that helps.

---

### Post by Bluebearbevis on 2010-11-26
Good Morning All,

I am happy for you lesannkel, but your suggestion didn't work for me.  The lightning add-on from "get add-ons" is not compatible with my Thunderbird build type (linux_x86_64-gcc3).  The lightning add-on build for 64 bit from elsewhere isn't compatible with firefox 3.6.12.  Is there not a lightning for both?  Or, again, is it possible to install the add-on to Thunderbird only?  Thanks everyone, hope you all enjoyed your turkey day.

Richard

---

### Post by Bluebearbevis on 2010-11-27
Hey Everyone,

Just wanted to say thank you for the support.  "Void" (name changed for confidentiality purposes) and others gave me a link and instructions (right click,save as link, etc...) on a similar thread and I now have a calendar!  How do you get that bracketed "Solved" deelee?:popcorn:
Anyway,

Richard

---

### Post by Crusty Old Fart on 2010-11-29
> **Bluebearbevis said:**
> Hey Everyone,

... How do you get that bracketed "Solved" deelee?:popcorn:
Anyway,

Richard

[SIZE=2]**[How to mark your thread as [SOLVED]]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6")**[/SIZE]

[B][COLOR=Green]Also, it would help if you posted at least a link to the solution that worked for you so others reading this thread could be helped as well.

Perhaps it was similar to this:
[/COLOR][https://addons.mozilla.org/en-us/thunderbird/addon/2313/reviews/256196/](https://addons.mozilla.org/en-us/thunderbird/addon/2313/reviews/256196/)[/B]

---

