---
title: "Controlling Print Quality When Printing From a Terminal"
date: 2009-10-19
forum: General Help
---

### Post by hamdev on 2009-10-19
I tried printing a manpage. The following prints the wine manpage on my Officejet printer:

man wine | lpr -P Officejet 

BUT: I want to control the print quality. Executing
lpoptions -d Officejet -l

produces the following line among others:

OutputMode/Print Quality: *Normal Draft Best Photo FastDraft

How do I specify a print quality of Best?

I have tried -o PrintQuality=Best and -o Printquality=Best and -o printquality=Best and printquality=best,
but the printout is always the same (I assume the default [Normal]).
I even tried -o OutputMode=Best and -o Outputmode=Best, but those didn't work either.

Now would I really want to print a manpage with a print quality of Best? Of course not, but I am testing this way so that I know that I have specified the right option, which I haven't.

---

### Post by Giblet5 on 2009-10-19
> **hamdev said:**
> I tried printing a manpage. The following prints the wine manpage on my Officejet printer:

man wine | lpr -P Officejet 

BUT: I want to control the print quality. Executing
lpoptions -d Officejet -l

produces the following line among others:

OutputMode/Print Quality: *Normal Draft Best Photo FastDraft

How do I specify a print quality of Best?

I have tried -o PrintQuality=Best and -o Printquality=Best and -o printquality=Best and printquality=best,
but the printout is always the same (I assume the default [Normal]).
I even tried -o OutputMode=Best and -o Outputmode=Best, but those didn't work either.

Now would I really want to print a manpage with a print quality of Best? Of course not, but I am testing this way so that I know that I have specified the right option, which I haven't.

When you say "that didn't work", how do you know?

Draft-photo would exceed your eye's ability to tell a difference on a printed man page...

I just tried man ls | lpr -poPrintoutMode=Best and it appears to be printing in Best mode (very slow, very clear, lots of ink wasted).

---

### Post by hamdev on 2009-10-20
> **Giblet5 said:**
> When you say "that didn't work", how do you know?

Draft-photo would exceed your eye's ability to tell a difference on a printed man page...

I just tried man ls | lpr -poPrintoutMode=Best and it appears to be printing in Best mode (very slow, very clear, lots of ink wasted).

I have done more testing today. If I set OutputMode to Photo, printing is extremely slow, and as you mention, wastes a lot of ink. If OutputMode is set to Draft, Normal, or Best, printing is fast (same speed for all), and I cannot tell the difference in output quality.

I ran the same tests using my other printer (an HP Photosmart 7960) and received identical results. The reason I had said that it didn't work is because performing a similar test using Windows XP results in increasingly better output and increasingly longer print times as I increased print quality.

I have my answer now, so I consider this closed. Thanks for the help.

---

