---
title: "Cimpiz from git?"
date: 2009-08-16
forum: General Help
---

### Post by detroit/zero on 2009-08-16
Is there a modern how-to for downloading & compiling the latest & greatest compiz version?

Everything I can find here is going on two years old. All the scripts are abandoned. Half the git url's are 404. Even the Compiz forums are horribly out-of-date.

Does anybody know anything?

---

### Post by Milos_SD on 2009-08-16
There is one script that is not abandoned and I'm using it. Right now compiz devs are porting code to c++ (compiz++), so 0.8.3 is the newest "old" version of compiz. :)
If you want you can make the script download and install compiz++ version (0.9) but don't do it just yet. It's not all ported, so you will have bugs and lack of plugins. :)
I hope you have git installed, so I don't have to tell you to install it.

First step is to download the script:

1) git clone git://anongit.compiz-fusion.org/users/omega/scripts

When that is downloaded, go to scripts directory:

2) cd scripts

There you will have a script named git-compiz.sh.

3) ./git-compiz --help to see what options there are. You would probably need to use:

4) ./git-compiz purge (it will delete any compiz files you have on your system.

5) Then use ./git-compiz --check-dep for script to install any missing deps you don't have.

6) Final step is to just start: ./git-compiz and let it do the magic. :)


P.S. I never figured out how to make it update, build and install compiz when you have it installed already, so it is the best just to do: ./git-compiz --purge ; delete scripts folder, and do the steps all over again. :)

---

