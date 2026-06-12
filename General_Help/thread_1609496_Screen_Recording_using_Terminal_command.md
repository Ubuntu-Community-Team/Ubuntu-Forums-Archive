---
title: "Screen Recording using Terminal command"
date: 2010-10-30
forum: General Help
---

### Post by timeoutmode on 2010-10-30
Hi guys,,

Can somebody please tell me the code when recording a screen using terminal command? it has this code "xllgrab".. that's all i can remember.. i read it somewhere in this forum and it really works but i can't find that thread anymore.. Please..

Thanks.

---

### Post by bobwyajnr on 2010-10-30
> **timeoutmode said:**
> Hi guys,,

Can somebody please tell me the code when recording a screen using terminal command? it has this code "xllgrab".. that's all i can remember.. i read it somewhere in this forum and it really works but i can't find that thread anymore.. Please..

Thanks.

Hi

Not sure if you mean video or screenshots (:oops: details, details, details :oops:). Do people get fatigued typing these days or something?? :)

I had a fun 2 weeks investigating grabbing screenshots from Windows games running under WINE last month:
[Official WINE Screenshot thread]("http://ubuntuforums.org/showthread.php?t=1601834")
That BASH script worked a treat for me and seemed to avoid most of the 'frame tearing' problems I had using the **PRINT-SCREEN** key.


Bob

---

### Post by timeoutmode on 2010-10-30
sorry. i'm a little sleepy. it's 6am here.. anyways i finally found the thread.. here is the command.

[HTML]ffmpeg -f x11grab -s 1024x768 -r 15 -i :0.0 -s 1024x768 -r 15 -sameq video.avi[/HTML]

---

### Post by mubtasim123 on 2011-04-02
:)I was looking for the same thing but when I use the code it doesn't record my voice. Is there any command that will make screen-caste with voice?:confused::guitar:

---

