---
title: "Medical software (record keeping) for Linux"
date: 2009-08-29
forum: General Help
---

### Post by absolutezero1287 on 2009-08-29
I work at an OB/GYN clinic and my boss wants to go paperless. However, I heard that software to keep records and things like that has to be approved by some federal agency or by the insurance companies. (I live in the US, btw). I was thinking of using something like MySQL to help her keep records but apparently I can't just "implement my own system" unless its approved.

So what I'm asking is do any of you guys know any (approved) software used to keep (and backup) medical records?

On a sidenote, I was thinking of using a cronjob with something like rsync to keep backups of all the files on a separate machine. However, it turns out that keeping backups is also highly regulated. Its very frustrating.

---

### Post by slacker1965 on 2009-09-27
Nothing?  Nothing?  Bump!  I am curious about this, too.  Is this something else that Microsoft is going to get an anchor in without anything from the Ubuntu community, or the larger Linux community?  Please say it ain't so...

---

### Post by absolutezero1287 on 2009-09-27
I guess that no one knows about this.

Its a shame.

---

### Post by mike555 on 2009-09-27
if you search you will find some , like ...   [http://www.oemr.org/](http://www.oemr.org/)   ,or ...   [http://sourceforge.net/projects/freemed/files/](http://sourceforge.net/projects/freemed/files/)      ..... I haven't tried it ...

---

### Post by slacker1965 on 2009-09-27
FWIW, I found these sites:
[INDENT]  [http://linuxmednews.com/](http://linuxmednews.com/)
  [http://www.debian.org/devel/debian-med/](http://www.debian.org/devel/debian-med/)
[/INDENT]I am not in the medical field, but I am a Linux enthusiast/promoter, and part-time programmer/software dabbler.  I hope this helps...

---

### Post by grturner on 2009-09-27
there is a dental system called openDental, it is compiled on C# and supposedly runs under the mono runtime. It implements sql. I'm not that familiar with it. I hate to tell you, but you're best off just sticking with the brand name stuff. I've looked seriously around for practice management software for a dental practice, but it just doesn't really exist. I remember there are some online based stuff that runs from a browser. My concerns there would be that even though it is encrypted, that's just too much liability if something were to happen.

---

### Post by slacker1965 on 2009-09-27
Thanks Mike555.  OpenEMR seems to be something worth a look.  I have checked it out briefly, played witht he demo a bit, and it seems to be a fully functional system.  However, it may not support absolutely everyone's needs.

---

### Post by absolutezero1287 on 2009-09-27
Open EMR looks promising.

---

