---
title: "is the PPA from Libre Office to be considered safe ?"
date: 2011-07-06
forum: General Help
---

### Post by Joris Donders on 2011-07-06
The website from Webup8 showed a way to get the newest, more stable version, Libre office via a PPA-channel. 

On the Dutch forum it was received as a high risc for breaking up your system (the upgrade was intended for 11.04: logic that was the version that has Libre Office installed). 

Now I feel that these warnings were at least a bit hasty, knowing that Libre Office has an intention for getting more involved for the professional market, so I feel that these software-makers will not be responsible for breaking up an entrire OS. 

Of course, every update - upgrade has riscs, I was wundering for getting a more professional answer; 
I feel that THIS ppa has a hugh potential for getting faster stable and improved versions for Ubuntu. 

So, are these warnings (ppa's can be responsible for breaking up your system) pausible, and more are these warnings correct for the PPA from Libre Office ? 

Thank you for reading this issue.

---

### Post by grahammechanical on 2011-07-06
This is not a professional answer. I am sorry.

I think that there is a contradiction between the words 'latest' and 'stable.' I think that a PPA will give you the latest and improved version a lot sooner than the Canonical repositories would. But I do not think that the latest and improved version is necessarily stable.

I had a certain issue with Openoffice where it took many minutes to go from the first record in the database to the last. An updated version improved this issue but another upgrade brought the problem back and it has carried over into Libreoffice. Some say the answer is to go back to an earlier set of libraries.

I would suggest that you should think of a PPA as a way of testing the latest, most up to date version. Others with a more professional opinion might have a different view.

Regards.

---

### Post by nomko on 2011-07-06
> **Joris Donders said:**
> The website from Webup8 showed a way to get the newest, more stable version, Libre office via a PPA-channel. 
 
On the Dutch forum it was received as a high risc for breaking up your system (the upgrade was intended for 11.04: logic that was the version that has Libre Office installed). 
I know that Dutch forum and i know who's there to be found. Bunch of so called and self proclamed arrogant Ubuntu "guru's" who cannot give a direct and correct answer (most answers you get there starts with: did you try.... or try this....). Thanks god i'm not there anymore.
 
>  
Now I feel that these warnings were at least a bit hasty, knowing that Libre Office has an intention for getting more involved for the professional market, so I feel that these software-makers will not be responsible for breaking up an entrire OS. 
 
Of course, every update - upgrade has riscs, I was wundering for getting a more professional answer; 
I feel that THIS ppa has a hugh potential for getting faster stable and improved versions for Ubuntu. 
 
So, are these warnings (ppa's can be responsible for breaking up your system) pausible, and more are these warnings correct for the PPA from Libre Office ? 
 
Thank you for reading this issue.
 
I've added the PPA of libreoffice from this site: [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)
 
I consider this site (launchpad.net) as safe and reliable. I never had any trouble on my system due to adding PPA's from the launchpad site. 
 
As long as you stay to the stable version, you can be pretty sure that nothing serious will happen.

---

### Post by Jouke74 on 2011-07-06
Ubuntu 10.04 comes with Openoffice not Libreoffice. IMHO you first need to completely purge Openoffice plus it's dependencies. Configuration files from Openoffice may mess up Libreoffice and the other way around. The same goes for plugins which can be used in both programs. 

After that you can add the ppa and then install Libreoffice. How much more stable this version is going to be, is the big question. Also with further updates from the ppa's (in either openoffice or libreoffice) you may loose this stability again. 

There are numerous dependencies, and running the latest Libreoffice on a somewhat older distro might cause issues. 

As with all Linux stuff, these issues are usually fixable, and no one can say how well this works on your system. You can make a backup, and install libreoffice (I have also heard of people having them running side by side).

Your time, your choice and evaluation if it is a necessity.

From my own experience it was quite easy to upgrade from Openoffice to Libreoffice (using the DEB's not ppa). However going back to Openoffice after installing Libreoffice messed up my system quite badly.

---

