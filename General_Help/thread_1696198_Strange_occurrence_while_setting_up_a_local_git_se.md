---
title: "Strange occurrence while setting up a local git server"
date: 2011-02-27
forum: General Help
---

### Post by Tystick86 on 2011-02-27
I recently put Ubuntu 10.10 server on my old pentium 3 and one of the things I wanted to do was set it up to be my own personal git hub.

I followed this tutorial at:
[http://tumblr.intranation.com/post/766290565/how-set-up-your-own-private-git-server-Linux](http://tumblr.intranation.com/post/766290565/how-set-up-your-own-private-git-server-Linux) and it works as advertised.

Now I can now push my repository to the server which is great but I was under the impression it would copy all the files but in only looks like my .git directory of the repository I sent. Sorry if I am phrasing this poorly. When I issue

$ git push origin master

I want it to act like heroku and not only push the git files but some how extract them so I can use it to quickly upload my rails apps onto my server. Does any one know how to accomplish this.

Please and thank you

P.S

I forgot to mention the strange occurrence while I was following the tutorial it said to

$ sudo chmod 600 /home/git/.ssh/*

which gave the error directory or file does not exist. I knew it existed so I logged out of the user I was using and into the user git and sure enough I could not only see the file but I could successfully change the permissions. I was wondering if any one knows why sudo was unable to see or manipulate the file but the user git was.

---

### Post by Tystick86 on 2011-03-08
So the answer was clone. Sorry about the poor phrasing of my question but if any one stumbles around with the same question clone is how you take a git repository and make a directory structure out of it.

Still don't under stand the sudo thing if any one has any insights.

---

