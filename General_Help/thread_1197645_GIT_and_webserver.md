---
title: "GIT and webserver"
date: 2009-06-26
forum: General Help
---

### Post by Belerophon on 2009-06-26
Hi.

I've just created a remote GIT repo, using Gitosis. The remote machine is also running a webserver.

So, I'm now able to pull and push things there...

The thing is that, remotely, GIT doesn't seem to keep my original files, but it seems to pack them (!?)
....so what I have locally is not what I have remotely.

The project I'm controlling under GIT is a website. So my objective was to put online automatically any modification to the code:
1 - I change code locally;
2 - I push to the remote repo
3 - The webserver in the remote machine reads the repo and my site points automatically to the newest changes in the code.

How do I point my webserver to the files of the repo?
Can anyone help? 

Thanks!

---

### Post by timvoet on 2009-06-26
you could setup a post-commit hook that upon commit checks out your code to another directory that your web server uses.  

Git doesn't maintain "files" as you think, it maintains diffs on files.

take a look in your <repo>/hooks

hope that helps

---

### Post by Belerophon on 2009-06-26
After some research, I have seen that git does not store files when the repo is created with --bare. 

I've also read that gitosis expects bare repos, so it's not a good idea to change to normal repo. 

...is this true?

If it is, I will probably write a post-commit hook as timvoet wrote.

Thanks.

---

