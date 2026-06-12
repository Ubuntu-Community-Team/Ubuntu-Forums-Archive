---
title: "BASH Shows Control and Escape Characters/Sequences"
date: 2009-12-27
forum: General Help
---

### Post by ghostknife on 2009-12-27
Since I installed Karmic, my bash terminals show "^C" when I press ctrl+c (even though ^C is interpreted), as well as escape sequences in SSH banners. I don't think it's terminal related, since from the same shell I can login to a working machine and have everything work as intended. Take this demonstration for instance. I added comments (prefixed with #) next to each line to describe what's happening.

```
quintin@quintin-VIAO:~$ ^C             # pressed ctrl+c
quintin@quintin-VIAO:~$ ^C             # pressed ctrl+c
quintin@quintin-VIAO:~$ cat
^C                                      # pressed ctrl+c
quintin@quintin-VIAO:~$ ssh 10.0.0.85  # login to working bash
\033[44mTest color\033[0m              # esc seq. instead of colors
quintin@10.0.0.85's password: 
Last login: Sun Dec 27 16:26:59 2009 from 10.0.0.145
quintin@akruger-laptop:~$              # pressed ctrl+c
quintin@akruger-laptop:~$              # pressed ctrl+c
quintin@akruger-laptop:~$ cat
                                        # pressed ctrl+c
quintin@akruger-laptop:~$ ssh 10.0.0.85
Test color                              # now it shows the colors
quintin@10.0.0.85's password: 

quintin@akruger-laptop:~$ 

```

Basically what happens here is to demonstrate the problem on the affected machine. I press ctrl+c at the prompt twice, then also inside a "cat" instance. Both times ^C has the desired effect, but it displays '^C' on the terminal. Then I log into a machine which works as desired. This machine has an SSH banner with colors. When the banner is shows, instead of colors the escape sequences themselves are shown. Once logged in I repeat all the same steps to show that they are now working as intended.

Any ideas?

---

### Post by ghostknife on 2009-12-27
I have noticed doing "stty -echoctl" makes it not print "^C" when pressing ctrl+c at a prompt. Though it prints a unicode character square when pressing it during a running program, for ex. cat/ping. Same with other escape characters. 

Example:
[IMG]http://imagebin.ca/img/mXbutJ1.png[/IMG]

Further. All my other machines have "echoctl" set, though they don't print ^C. How else could you have this character NOT print?

And, running screen/xterm, the unicode characters aren't printed when I disable echoctl. I don't think it's a gnome-terminal font issue, because running the screen session inside the same shell will NOT print the unicode square.

---

### Post by dcstar on 2009-12-27
> **ghostknife said:**
> Since I installed Karmic, my bash terminals show "^C" when I press ctrl+c (even though ^C is interpreted), as well as escape sequences in SSH banners. I don't think it's terminal related, since from the same shell I can login to a working machine and have everything work as intended. Take this demonstration for instance. I added comments (prefixed with #) next to each line to describe what's happening.
........
Any ideas?

Check the TERM setting.

---

### Post by john newbuntu on 2009-12-27
Add this in your .bashrc:
```
stty -ctlecho
```

---

### Post by ghostknife on 2009-12-29
I have also suspected the term setting, but I'm not sure what else it could be.

Mine is xterm on all my machines, even the working ones. What should the term setting be?

---

### Post by ghostknife on 2009-12-29
I have also suspected the term setting, but I'm not sure what else it could be.

Mine is xterm on all my machines, even the working ones. What should the term setting be?

---

