---
title: "Thunderbird Ligthning problem"
date: 2011-04-26
forum: General Help
---

### Post by snarf77 on 2011-04-26
Hi all,

I'm encountering very embarassant problem with thunderbird (3.1.8) and lightning (1.0b2) on a ubuntu 10.10 distro.

Indeed, lightning was configued properly to work with a google agenda without problem till today but now each time I open thunderbird I got 4 blank pop up window without content (one is displaying a title "data import" (this is a french translation so perhaps not the exact label) and finally when thunderbird opens, I can't see my calendar in the agenda tab.

More strange is that some of my appointments linked to this agenda is nevertheless displayed (and some are lost..).

As the original data were at goolle, I decided to delete both "lightning" and "provider for google agenda" add on from thunderbird and reinstall them. Unfortunately I got same problem at thunderbird start... I also tried to declare again my agenda as a new one, but Thunderbird told me it is aleady registered ....

There is some hared links written seomwhere I can't break or update... Does someone ever encounter this problem or do you know how to properly remove lightning from thunderbird ??

Many thanks in advance for your help as this for a professionanl use and this is very annoying...

Snarf

---

### Post by cavalier911 on 2011-04-26
The local user configuration/profile may be the cause of problems.
This is not removed or modified when you remove/reinstall programs. 
The location for thunderbird is ~/.mozilla-thunderbird
My advice is to reboot, open terminal, and launch thunderbird with this command:
```
thunderbird -ProfileManager
```
Thunderbird-Choose User Profile
Click** Create Profile...** button
Leave the old profile for now.
Double click the new profile or highlight and click Start Thunderbird button.
You're starting with a clean slate,all servers and settings must be reconfigured.
No plugins/addons are installed.
Lightning is beta software.
Beta software is unstable and has bugs.

---

