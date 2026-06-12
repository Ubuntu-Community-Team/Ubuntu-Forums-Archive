---
title: "Launching Matlab from Bash Script"
date: 2012-01-03
forum: General Help
---

### Post by slichto3 on 2012-01-03
I'm working on writing a Bash script that will call Matlab functions.  I've been using the following command to do this:

matlab -nojvm -r 'whateverCommand'

That's worked pretty well, but I'm running into problems when I want to call Matlab, then change directories, at least when the directory contains Bash variables.  For example:

foldernum=50001
mypath=/home/work/$foldernum
matlab -nojvm -r 'cd $mypath'

The above code won't perform the way I'd like it to.  Matlab will go to /home/work, but will not go to /home/work/50001/.  It doesn't seem to recognize what $foldernum is, even though when I echo $mypath, I get /home/work/50001. 

I'd really appreciate any help, I'm getting a bit frustrated with this problem.

Thanks.

---

