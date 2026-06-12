---
title: "How to run Shell Script from a browser!"
date: 2010-04-18
forum: General Help
---

### Post by Face_Man on 2010-04-18
hello all,

How to run Shell Script from a browser using External Protocol request ?

i try this however it did work
```
  
          < a href="sh:/path/of/my/script.sh"  >YourLinkText< / a >

```

Any help would be much appreciated.

---

### Post by Dayofswords on 2010-04-18
whatcha up to?




(as this sounds kinda malicious. but hey, what do i know?)

---

### Post by new_tolinux on 2010-04-18
> **Face_Man said:**
> hello all,

How to run Shell Script from a browser using External Protocol request ?

i try this however it did work
```
  
          < a href="sh:/path/of/my/script.sh"  >YourLinkText< / a >

```Any help would be much appreciated.
You should not be able to do so.

At first, browsers are meant to display things that the webserver serves to the browser.
Second is, that hyperlinks are processed by the browser, not by the webserver. That way, /path/of/my/script.sh should be on the machine you use for browsing (the "client").

Because you use a browser, you're not allowed (in general) to check for that file to exist, neither to check the contents of that file.

Although there _are_ ways with javascript to access certain files in Internet Explorer (modify, not execute), you _will_ get a security-warning. Would be a bad thing if you didn't.
For FF/Chrome, no idea, I know they don't support as much of the javascript than IE. Probably it won't even work in FF/Chrome.

Let's assume that you're using this _only_ for your private LAN. If not, it should be reported to a mod and closed because then it becomes a serious threat which to me is a way of hacking into other peoples systems.

---

### Post by Face_Man on 2010-04-18
well,
thx for replying, my problem is i have a list of shell scripts that i know where there are(list them in html file)! and i would like to be able to execute them by click on the link. i know there is a way to run an App using a browser (fake protocol) however the program have to be install in your local PC .

---

### Post by new_tolinux on 2010-04-18
_If_ the scripts are marked as "executable" on your local machine, then you should use the file:///path/to/script.ext handler and choose to open them.
I don't know how you should do the /path/to/script.sh part exactly, in Windows it was file://c:/path/to/script.ext but Linux doesn't know any drive-letters. For linux you'll have to find that one yourself.

---

### Post by john newbuntu on 2010-04-18
should be as simple as starting from "file://" and hit enter. Then traverse the tree.

---

