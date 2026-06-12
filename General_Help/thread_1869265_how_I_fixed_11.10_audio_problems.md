---
title: "how I fixed 11.10 audio problems"
date: 2011-10-25
forum: General Help
---

### Post by giuspen on 2011-10-25
I have a packard bell EasyNote LJ75, had problems with audio in/out.
After I run the following command the problem was fixed:
```
killall pulseaudio; rm -r ~/.pulse*
```
Hope this helps somebody else with the same trouble.
Cheers.

---

### Post by Neoncamouflage on 2011-10-25
I'm having similar problems, what exactly does this command do? I'm generally wary of killing/removing things before I know why.

---

### Post by ubupirate on 2011-10-25
> **Neoncamouflage said:**
> I'm having similar problems, what exactly does this command do? I'm generally wary of killing/removing things before I know why.

I believe it resets Pulseaudio, from what I've seen on Google search with the command.

[http://www.google.com/search?hl=en&source=hp&biw=1280&bih=861&q=killall+pulseaudio%3B+rm+-r+%7E%2F.pulse*&oq=killall+pulseaudio%3B+rm+-r+%7E%2F.pulse*&aq=f&aqi=&aql=1&gs_sm=e&gs_upl=5763l5763l0l6461l1l1l0l0l0l0l127l127l0.1l1l0](http://www.google.com/search?hl=en&source=hp&biw=1280&bih=861&q=killall+pulseaudio%3B+rm+-r+%7E%2F.pulse*&oq=killall+pulseaudio%3B+rm+-r+%7E%2F.pulse*&aq=f&aqi=&aql=1&gs_sm=e&gs_upl=5763l5763l0l6461l1l1l0l0l0l0l127l127l0.1l1l0)

---

### Post by giuspen on 2011-10-25
> **ubupirate said:**
> I believe it resets Pulseaudio, from what I've seen on Google search with the command.

[http://www.google.com/search?hl=en&source=hp&biw=1280&bih=861&q=killall+pulseaudio%3B+rm+-r+%7E%2F.pulse*&oq=killall+pulseaudio%3B+rm+-r+%7E%2F.pulse*&aq=f&aqi=&aql=1&gs_sm=e&gs_upl=5763l5763l0l6461l1l1l0l0l0l0l127l127l0.1l1l0](http://www.google.com/search?hl=en&source=hp&biw=1280&bih=861&q=killall+pulseaudio%3B+rm+-r+%7E%2F.pulse*&oq=killall+pulseaudio%3B+rm+-r+%7E%2F.pulse*&aq=f&aqi=&aql=1&gs_sm=e&gs_upl=5763l5763l0l6461l1l1l0l0l0l0l127l127l0.1l1l0)

yes it just resets pulseaudio.
don't worry using the command, you don't even require admin rights, after that just reboot if you have problems (I don't remember if I did reboot or not, probably yes).
this solution does not come from me but was inspired from [http://dharmendralinuxdiary.blogspot.com/2011/10/ubuntu-1110-sound-problem.html](http://dharmendralinuxdiary.blogspot.com/2011/10/ubuntu-1110-sound-problem.html) from whom I took only the latest part since didn't want to add strange repositories and do any dist-upgrade.

---

### Post by st.lzack_09 on 2011-11-04
thanks....
it solved my problem :D

---

