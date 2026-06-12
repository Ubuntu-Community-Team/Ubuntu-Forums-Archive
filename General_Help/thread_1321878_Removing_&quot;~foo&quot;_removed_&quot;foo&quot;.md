---
title: "Removing &quot;~foo&quot; removed &quot;foo&quot;"
date: 2009-11-10
forum: General Help
---

### Post by amn108 on 2009-11-10
I have just witnessed my home directory disappear in front of my eyes, and I cannot figure out what is it I did to deserve that.

I have my account home directory in /home/amn and from previous installations a /home/~amn lingering (my old files). To clean up some hard drive space, I did "rm -r /home/~amn" as root, but when the command finished, /home/amn is all but empty!

I have backups thankfully. How did this happen? Is tilde character some form of pattern? Hope not.

---

### Post by andrewc6l on 2009-11-10
I'm not sure what the bash substitution would be, but ~ usually stands for your home directory. If you are user foo, then both ~ and ~foo refer to /home/foo/.

However /home/~foo should not refer to the same directory. (At least it doesn't on bash - not sure what dash will do.)

---

### Post by amn108 on 2009-11-11
Well, it turned out that the tilde was only expanded for my username - 'amn'. Doing 'cd ~amn' from wherever had the same effect as 'cd /home/amn' BUT only when tilde was followed by 'amn'. Doing 'cd ~foobar' actually assumed a directory called literally '~foobar'. I am sure bash was involved in this.

Anyways, this little decision on Canonicals part has arguably cost me my entire home directory. Now, I know this sounds like "why do you blame someone else for your own bad mistakes?", but truly the tilde should either expand or not. Doing so on case by case basis - i.e. expanding it to '/home/' for 'cd ~amn' but taking it for a literal for 'cd ~foobar', as clearly evidenced, only brings confusion and I am sure others will perhaps end up doing the same mistake.

To clarify further, I knew that tilde is a shortcut to home directory, but I always wrote 'cd ~/Desktop' f.e. when I actually expected it to expand. At least if it expanded to '/home/amn' then 'cd ~amn' should have said 'bash: cd: /home/amnamn: No such file or directory'. 

I am just saying the behaviour of this is way too undeterministic.

---

### Post by mr_steve on 2009-11-11
Here's the thing. ~ always refers to the home directory. ~foo always refers to the home directory of user foo. Ever seen a web address like foo.com/~bar?

To summarize; a naked '~' refers to the current user's homedir.
a '~' followed by a username, refers to that user's homedir.

This has been a Unix convention for probably 30+ years.

Sorry for your loss, but you can't really blame Canonical for this one. You really need to know exactly what you're doing when using shell expansions like ~ or *.

Also, you probably shouldn't name files or directories starting with a ~.

To specify a literal '~', like if you want to delete a file simply named '~', you must escape it with a backslash, i.e. "rm \~"

Again, sorry this happened, but I hope this helps you understand why, and avoid it in the future.

---

### Post by amn108 on 2009-11-11
You are absolutely right. I thought it was strange that it did not expand '~~amn' but now I see that it only expands if a tilde is followed by an alpha-num. And only if the user exists - in my case there is no user named 'foo' and doing 'cd ~foo' tells me "bash: cd: ~foo: No such file or directory". Perhaps though, it WOULD expand if the directory existed?

---

