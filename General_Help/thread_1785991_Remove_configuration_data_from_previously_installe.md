---
title: "Remove configuration data from previously installed packages"
date: 2011-06-19
forum: General Help
---

### Post by sixcorners on 2011-06-19
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
You show how to remove a package and it's dependencies. You show how to remove the configuration from the package you are currently uninstalling. You don't show how to remove the configuration data from a package and all of it's dependencies. Why?

---

### Post by dcstar on 2011-06-19
> **sixcorners said:**
> [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
**You** show how to remove a package and it's dependencies. **You** show how to remove the configuration from the package you are currently uninstalling. **You** don't show how to remove the configuration data from a package and all of it's dependencies. Why?

Who is "you" and who do YOU think is going to read this?

---

### Post by sixcorners on 2011-06-19
> **dcstar said:**
> Who is "you" and who do YOU think is going to read this?

Whatever organization maintains this stuff? Whomever wrote that specific section? Whomever answers questions here and berates them for not reading the documentation or searching for it first?
Who is going to read this? Isn't this the 3rd thing you would tell users what to do when they ask how to uninstall things? Do people uninstalling things not want to uninstall the things they want to uninstall?

---

### Post by amauk on 2011-06-19
It's a community run wiki

There's no central authority behind the community documentation, it's just users documenting useful stuff for the benefit of other users

If you want to make an amendment, add extra information or change the page in some other way, do so

---

### Post by sixcorners on 2011-06-19
> **amauk said:**
> It's a community run wiki

There's no central authority behind the community documentation, it's just users documenting useful stuff for the benefit of other users

If you want to make an amendment, add extra information or change the page in some other way, do so

I pledge to amend the wiki page if I ever find out how to use the apt-get utility to do what I want it to do.
apt-get autopurge
apt-get purge `apt-get list configured`
apt-get purge configured
All seem like things that you should be able to do with a package management tool. It seems however that you can't even use it to list your installed packages.

---

### Post by amauk on 2011-06-19
> **sixcorners said:**
> I pledge to amend the wiki page if I ever find out how to use the apt-get utility to do what I want it to do.
apt-get autopurge
apt-get purge `apt-get list configured`
apt-get purge configured
All seem like things that you should be able to do with a package management tool. It seems however that you can't even use it to list your installed packages.Oh, sorry
I thought you were complaining about the documentation

This should do
```
dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg --purge
```

**dpkg -l** lists all installed packages
**grep '^rc'** filters the results to only those with a remaining config
**awk '{print $2}'** grab the package name
**xargs dpkg --purge** pass to dpkg for purging

---

### Post by sixcorners on 2011-06-19
> **amauk said:**
> Oh, sorry
I thought you were complaining about the documentation

This should do
```
dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg --purge
```

**dpkg -l** lists all installed packages
**grep '^rc'** filters the results to only those with a remaining config
**awk '{print $2}'** grab the package name
**xargs dpkg --purge** pass to dpkg for purging

I was complaining about the documentation a little.. Do you think it would be helpful if I added that to the wiki page? Because it isn't something that is built in I guess you all don't think that a lot of users would want to do this but I consider it as one of the top things to do when uninstalling stuff..
Anyway, thanks both of you for the help.. Sorry if I came off as a jerk.. I just kind of don't like certain things about these popular package management systems.. I find them frustrating..
That command line wizardry is pretty neat.. I didn't know about awk and xargs.. I also didn't know that dpkg showed the state of packages that easily..
Anyway thanks again. That did exactly what I was looking for.

Heh.. I think I would have found it pretty funny if someone came in here and tried to troll me with a disguised fork bomb or something.. With the way I was acting I was kind of expecting it and was running that line one segment at a time..

---

### Post by amauk on 2011-06-19
Also, the GUI way would be

Open Synaptic Package Manager
Click the "Status" button (group packages by status)
Select the "Not installed (residual config)" status
Highlight all packages
Purge

> **sixcorners said:**
> Do you think it would be helpful if I added that to the wiki page? Because it isn't something that is built in I guess you all don't think that a lot of users would want to do this but I consider it as one of the top things to do when uninstalling stuff..Yeah, you can if you want
I think the ability to uninstall something, reinstall it later (maybe many months down the road) and have all your previous config intact is more of an end-user benefit than saving a few kilobytes here and there by purging the config files, but opinions will, of course, differ

---

### Post by sixcorners on 2011-06-19
I mainly wanted to get rid of the configuration data because I didn't know how to get rid of the mysql databases a package had created (or even if they were still there).. I also configured something with some mail program that I kind of guessed at. I understand that there will be configuration information that needs to not be touched.
Edit: Thanks for the synaptic information btw.
The deed is done: [https://help.ubuntu.com/community/AptGet/Howto?action=diff&rev2=44&rev1=43](https://help.ubuntu.com/community/AptGet/Howto?action=diff&rev2=44&rev1=43)

---

