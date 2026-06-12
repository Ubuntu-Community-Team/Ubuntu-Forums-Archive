---
title: "Run command on completion of ssh session"
date: 2009-12-04
forum: General Help
---

### Post by hwttdz on 2009-12-04
So I have a few machines I work on that share a filesystem.  And it's somewhat annoying to have to browse back to my working directory after changing machines.  So I was trying to make a few modifications to ssh, bash_profile, bash_logout and the exit command to fix this little hitch. 

Anyways, I currently have it set up such that ssh does

echo "cd $PWD" > ~/.pwd # make script for changing to current directory
/usr/bin/ssh "$@" # execute the ssh command as asked

then .bash_profile does
source ~/.pwd
which changes me to the directory I was in when ssh executed

then bash_logout does
echo "cd $PWD" > ~/.pwd

so when I exit the ssh session ~/.pwd contains a script to change to my working directory, but I can't figure out how to execute that after the ssh session terminates.  I tried appending it to my ssh script, after the ssh call, with the thought that it wouldn't be executed until the ssh command finished, somehow this is not the case.  

And exit is is bash builtin, which means it's harder to mess with aliases and whatnot.  Anyways suggestions are welcome.

Eventually I got the solution I outlined above working, I think it was just a typo in one of the files that was preventing it from working.

---

