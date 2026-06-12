---
title: "Concerning launchers when installing programs (MATLAB)"
date: 2010-02-25
forum: General Help
---

### Post by lewin on 2010-02-25
I've installed Matlab on Ubuntu 9.10. I followed the installation instructions from here:

[http://xinyustudio.wordpress.com/2009/09/24/install-matlab-on-ubuntu/](http://xinyustudio.wordpress.com/2009/09/24/install-matlab-on-ubuntu/)

but I created a launch icon here:

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

these two instructions tell you to install it in different folders, so my launch icon doen't work.

So when I click Applications->Programming-> Matlab2009b 

I get an error: Could not launch Matlab2009b. Failed to execute child process "matlab"(no such file or directory). It's probably that the launcher has a broken link to the executable matlab program, but I'm not sure how I'm supposed to redirect the launcher??

---

### Post by daliakopoulos on 2010-03-25
In case you haven't still figured this out:

gedit /usr/share/applications/matlab.desktop

and then edit the Exec line to 

Exec=/usr/local/matlab2009b/bin/matlab -desktop

... should work

---

### Post by flamacue on 2010-04-07
Thanks daliakopoulos, I was having the same problem.

Note for anyone else having this issue:  you don't have to use the command line (or a text editor) to modify the launcher.  Instead of doing it just like daliakopoulos suggested, I went in through System -> Preferences -> Main Menu ... and created and edited my launcher there.  Also, since I have my Matlab shortcut in my $PATH (it's in /usr/local/bin/), I don't even need the path in the "Command" field--just
```
matlab -desktop
```
will suffice.

See the attached picture for an illustration.  :)

Cheers.

---

### Post by eddyojb on 2010-04-10
Cheers for the tips guys.

I folllowed flamacue's steps and they worked nicely except that my Matlab launcher would only run properly if I chose to run it through the terminal.

Therefore for anyone else experiencing the same problem follow flamacues steps and in 'Launcher Properties' where it says 'Type:' choose 'Run Application in Terminal' , as opposed to just 'Application'.

Hope this helps

---

### Post by freefaling on 2012-05-08
> **daliakopoulos said:**
> In case you haven't still figured this out:

gedit /usr/share/applications/matlab.desktop

and then edit the Exec line to 

Exec=/usr/local/matlab2009b/bin/matlab -desktop

... should work

Thank you!

---

### Post by oldos2er on 2012-05-08
Old thread closed.

---

