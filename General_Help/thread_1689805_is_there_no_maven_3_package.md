---
title: "is there no maven 3 package?"
date: 2011-02-17
forum: General Help
---

### Post by tombrus on 2011-02-17
Hi,

I need to install maven 3 (not maven 2). 

I googled and googled but can not find any ref to a apt-get package containing maven 3.
Am I a bad googler or does it indeed not exist and need I go through a manual install?

Thanks,
Tom

---

### Post by jonycobain on 2011-03-18
I have the same issue. Any ideas? Thanks

---

### Post by r-senior on 2011-03-18
A quick look at my test 11.04 Natty system shows that Maven 2 is in the repositories but not Maven 3.

However, I note that the embedded Maven in the Netbeans 6.9 in the Natty respositories is Maven 3.0-SNAPSHOT, which is a partial, if not ideal, solution for Netbeans users.

It's no big problem installing Maven 3 from the zip file from Apache though is it? IIRC it's only a case of unpacking it somewhere under your home directory and adding the bin directory to your path/pointing your IDE at it.

---

### Post by skomp on 2011-08-24
yeah, but: no. actually i have the same issues over and over again and just come to the conclusion: ubuntu is not ment to be used by (java) developers. Java5 has been removed from the repositories (and whoever does serious eclipse plugin development needs that for compatibility reasons), there is no proper maven package, and some more issues i don't want to elaborate on. next time i reinstall (because ubuntu likes to **** up my wireless driver) it will definetively NOT ubuntu.

---

### Post by Mike Brennan on 2011-11-07
> **skomp said:**
> yeah, but: no. actually i have the same issues over and over again and just come to the conclusion: ubuntu is not ment to be used by (java) developers. Java5 has been removed from the repositories (and whoever does serious eclipse plugin development needs that for compatibility reasons), there is no proper maven package, and some more issues i don't want to elaborate on. next time i reinstall (because ubuntu likes to **** up my wireless driver) it will definetively NOT ubuntu.

I use Ubuntu for serious Java development without any difficulties. I don't have any problems with it. There are plenty of others who do serious Java development on Ubuntu. You are the first I've ever heard of who has been stopped dead in his tracks when he can't find what he needs in the repositories.

If you use Eclipse, you are much better off downloading it from the Eclipse website and installing it, then using its built-in update manager for additional plugins. That works just fine. You do not want to rely upon the Eclipse in the repositories.

For serious Java development, you are probably not going to want to rely purely on Java libs in the repositories. But then, if you are planning on using maven, there isn't any reason why you would want to (since that is what maven is for). It would be nice if there were a more up-to-date version of maven itself in the repositories, but I don't see that it is the end of the world to have to install the latest by other means.

---

### Post by biffta on 2012-01-31
OK come on people it's 2012 now, can we get maven 3 into the Ubuntu repo?

---

### Post by doobrie on 2012-01-31
I understand the pain of Java programming on Ubuntu, but find that the problems are only to do with package management - the benefits of developing on a *nix system far outweigh the problems of getting the IDE / tools etc. installed.

I agree that its a pain having to install Eclipse and Maven via downloads, but its very straightforward to do both and is over in a few minutes.

To me, these small things are not enough to stop me using Ubuntu for major Java development.

---

### Post by doobrie on 2012-01-31
> **biffta said:**
> OK come on people it's 2012 now, can we get maven 3 into the Ubuntu repo?

I've not tried this myself, but this looks like a possible way to install Maven 3 without a direct download.

[http://www.discursive.com/blog/4636](http://www.discursive.com/blog/4636)

---

