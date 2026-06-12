---
title: "Unity destroyed with NIS"
date: 2012-01-02
forum: General Help
---

### Post by phma on 2012-01-02
My Unity gets completely destroyed after having tried to login with a NIS user.
Let's back up:
I have ubuntu 11.10 workstation and users are usually managed by a NIS server and the home folder is mounted via NFS. Now, I can't remember having done anything unusual but I cannot login with as a NIS user and a local user gets a completely destroyed unity desktop after a login attempt by a NIS user. Then, only the file manager's top bar is displayed, no launcher bar, no logout buttons, nothing else.
I tried unity --reset, unity --replace in a shell but nothing helps.
I also tried
rm -rf $HOME/.compiz-1
rm -rf $HOME/.compiz/
rm -rf $HOME/.config/compiz-1
rm -rf $HOME/.gconf/apps/compiz-1
rm -rf $HOME/.gconf/apps/compizconfig-1
rm -rf $HOME/.cache/compizconfig-1

Any suggestions? And of course, I would really like to login to unity as a NIS user again! (Login via command-line (Ctrl-Alt-F1) works fine.)

---

### Post by phma on 2012-01-10
Okay, solved it myself. There was a quota limit on the nfs share that was exceeded. I deleted some files on the nfs. Now, the NIS user can log in again. However, I still do not understand how this can have effects on a local user account and the unity desktop.

---

