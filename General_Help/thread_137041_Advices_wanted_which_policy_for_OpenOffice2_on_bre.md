---
title: "Advices wanted: which policy for OpenOffice2 on breezy ?"
date: 2006-02-27
forum: General Help
---

### Post by tassou on 2006-02-27
Hi,

I am a ubuntu user and I need to use OpenOffice2 in production, on ubuntu systems. At the release of breezy, I have been using the beta version that came with it. After a couple of month of use, (and many crashes :) ), I decided to use the more up-to-date version provided by Doko on external repositories, currently 2.0.1. So far I have been satisfied of this choice as it fixed many instabilities, and because doko packages are of good quality and integrate very well in apt. Thank you doko for that.

Now I need to use OpenOffice bibliography facility. And I am facing a very big problem decribed here [http://ubuntuforums.org/showthread.php?t=131625](http://ubuntuforums.org/showthread.php?t=131625).
Basically I just can not use it as the database won't load, and this problem is probably related to the package of OOo2 I use. 

So now I have to find a solution in the following 2 weeks :). According to you, which one would be the best:
- downgrading to the default beta (not really an option actualy)
- use an external package, like the rpms provided by official website (which one ?)
- something else ? 

Thank you for help


Tassou

---

### Post by MartinG on 2006-02-27
I've had various problems with the Doko packages, as a result of which I now use the 2.0.1 version from the official website, converted with alien.  This has sorted out my problems (see a couple of threads I started with no responses), and I'd recommend it.

---

### Post by tassou on 2006-02-27
Hi MartinG,

Thank you for this information.
so you confirm that doing so you can access the bibliography from writer with no problem, using official 2.0.1 on breezy ?


Tassou

---

### Post by tassou on 2006-02-27
Hi,

well, as I had to find a working solution very quickly I removed doko packages and used official OOo rpm.
Now it works well, but I don't really like this solution, so I am still really interested by any suggestion

Thanks

---

### Post by MartinG on 2006-02-28
[QUOTE=tassou]Hi,

well, as I had to find a working solution very quickly I removed doko packages and used official OOo rpm.
Now it works well, but I don't really like this solution, so I am still really interested by any suggestion

Thanks[/QUOTE]Sorry not to have replied to post #3 earlier, glad you've found it does work.  What is it you don't like about this solution?  I've sorted out one of my niggles by copying the OOo Crystal icons to my "official" OOo (I use Kubuntu), so now it all works seamlessly.

BTW, you don't have to remove the doko packages; for a while I had the official and doko installations side-by-side.

---

### Post by tassou on 2006-02-28
[QUOTE=MartinG]  What is it you don't like about this solution? [/QUOTE]
Well, it's just not the debian way. I prefer to use official repositories and let mainteners do their work through them.

Thank you

---

### Post by MartinG on 2006-02-28
[QUOTE=tassou]Well, it's just not the debian way. I prefer to use official repositories and let mainteners do their work through them.

Thank you[/QUOTE]Yeah, I agree with you there.  But the OpenOffice maintainers seem to be set on rpm only packages, with debs left to kind souls like Doko to sort out on their own.  Inevitably some things are going to go wrong; it's lucky that alien is such an effective tool!

---

