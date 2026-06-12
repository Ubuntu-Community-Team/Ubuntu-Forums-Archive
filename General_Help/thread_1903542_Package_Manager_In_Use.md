---
title: "Package Manager In Use?"
date: 2012-01-02
forum: General Help
---

### Post by Maleificus on 2012-01-02
I am trying to install an application and it keeps telling me that the package manager is in use, so I restarted, I am still getting the same problem. Sometimes when I am trying to install something I get a message saying that my configuration may be broken.

---

### Post by KdotJ on 2012-01-02
What is the error message you're getting? Does it only appear when trying certain packages? I assume you're not updating anything in the background while trying to install these packages?

---

### Post by Maleificus on 2012-01-02
No, I am not trying to do any updating in the background, the messages I am getting are:
"The package system could not initialized, your configuration may be broken"
and
"Another application seems to be using the package system at this time. You must close all other package managers before you will be able to install or remove any packages"

---

### Post by bill23 on 2012-01-03
I am also getting that message?

---

### Post by ricky06181993 on 2012-01-03
I am also having this issue

---

### Post by AlexDudko on 2012-01-03
run
> top
find the process name and  PID which blocks package manager (it can be package manager itself when it checks for updates in the background).
> sudo kill PID
After that run
> sudo apt-get update && apt-get upgrade

---

### Post by Maleificus on 2012-01-04
Looking at all the processes that are running I do see that none of them are the package manager and there really is no way for me to tell what is "blocking" the package manager.

---

### Post by topsites on 2012-01-04
The problem with most folks (myself included) when it comes to Linux is right after we first install Linux we then go through that package / software manager browsing through all the software and installing anything and everything that looks like we might use it someday... Granted we try and use restraint but the fact is I have found this approach can do more harm than good, mostly because these are exactly the types of problems it tends to create.

So if at all possible I would start with a fresh install.
If nothing else works that is the ultimate solution, start over.

Then, only...
ONLY install an application if you absolutely HAVE to have it, meaning that you are about to USE it.
Nothing else.

Keep it clean, keep it simple, just like Windows an uncluttered Linux works best.

Trust me on this one :D

---

### Post by Maleificus on 2012-01-04
I only have installed the things that I am about to use. I am not like most others in the aspect if that is what other people do. My programs list is actually quite clean, that most installations that I have done are from playdeb.net with some games and stuff. Are you telling me I have to re-install Linux?

---

### Post by Maleificus on 2012-01-04
I fixed the issue. I ran sudo dpkg --configure -a because sudo apt-get update && apt-get upgrade told me it had a problem and that was the way to fix it. So I ran that command and now I have no issues with the Package Manager. Thanks for the help guys.

---

### Post by LeeM on 2012-02-21
Same thing happened to me. The update manager got stuck. After flailing around, I found the hint about 
sudo dpkg --configure -a
and it saved the day!!:p

---

### Post by Ballie on 2013-01-13
I too ran into this problem, and it always makes me happy to find others  that ran into, and solved the same problems that I encounter. The [FONT=Times New Roman]***"***_***dpkg --configure -a***_***"*** [/FONT]trick did it for me too.

Being  a linux novice, I find it very hard to remember the correct syntax when  I need them later, besides that, I don't like having to type more than I  need to, so to prevent me from having to look for this solution again  in the future, I decided to add them to my [FONT=Times New Roman]***"******~/.bash_aliases******"***[/FONT] file, and wanted to share this with anyone whom might be interested.

Here is de code for these aliases, feel free to give the functions and aliases another name if you want:

```

#functions
apt_config()
  {
    sudo dpkg --configure -a
  }

apt_update()
  {
    sudo apt-get update
    apt-get upgrade
  }

#aliases
alias apt-config='apt_config'
alias apt-update='apt_update'


```Don't you just LOVE aliases :biggrin:

---

### Post by oldos2er on 2013-01-13
> **Ballie said:**
> Don't you just LOVE aliases :biggrin:

I also love ```
history
```  :)

---

