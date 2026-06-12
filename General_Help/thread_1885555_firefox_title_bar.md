---
title: "firefox title bar"
date: 2011-11-23
forum: General Help
---

### Post by subehsharma on 2011-11-23
running Xubuntu 11.10. Anybody knows a way to remove the default system title bar which reads "website name" above the tabs row?

---

### Post by mike555 on 2011-11-23
click View, Toolbars and uncheck the ones you don't want to see......

---

### Post by subehsharma on 2011-11-23
not that..i'm asking about the title bar above the tabs

---

### Post by Toz on 2011-11-23
devilspie ([http://burtonini.com/blog/computers/devilspie/]("http://burtonini.com/blog/computers/devilspie/")) will do that. Here is a working configuration file:

```
$ cat ~/.devilspie/firefox.ds 
(if (is (application_name) "Firefox") and (contains (window_name) "Mozilla Firefox")
             (begin
                (undecorate)
             )

```

Other helpful links:
- [https://help.ubuntu.com/community/Devilspie]("https://help.ubuntu.com/community/Devilspie")
- [http://www.foosel.org/linux/devilspie]("http://www.foosel.org/linux/devilspie")

---

### Post by subehsharma on 2011-11-24
I installed devilspie and then execute the command u mentioned and this is what i got:

subsharm@subsharm-ThinkPad-T61:~$ cat ~/.devilspie/firefox.ds 
cat: /home/subsharm/.devilspie/firefox.ds: No such file or directory

---

### Post by LewisTM on 2011-11-25
Try Alt-F11. This will remove the window title and other decorations and run Firefox fullscreen. Type again to restore. This will not allow you to have no title bar in windowed mode. 
For that, you should use Google Chrome or Chromium. Or try one of the hacks proposed [here]("http://support.mozilla.com/en-US/questions/782155").
In fact, [this extension]("http://tiny.cc/hidec") seems to do the trick!

---

### Post by subehsharma on 2011-11-26
Wow..The extenstion is what i was looking for! Man, thanks a ton for advising it!!! Cheers...

---

### Post by Elfy on 2011-11-26
> **subehsharma said:**
> I installed devilspie and then execute the command u mentioned and this is what i got:

subsharm@subsharm-ThinkPad-T61:~$ cat ~/.devilspie/firefox.ds 
cat: /home/subsharm/.devilspie/firefox.ds: No such file or directory

For anyone else - you need to actually have created the file for it to work 

```
gedit ~/.devilspie/firefox.ds
```

and copy in the information.
```

if (is (application_name) "Firefox") and (contains (window_name) "Mozilla Firefox")
             (begin
                (undecorate)
             )
```

---

### Post by subehsharma on 2011-11-29
Thanks everyone for your responses/suggestion! :-)

---

