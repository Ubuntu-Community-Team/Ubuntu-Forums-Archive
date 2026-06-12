---
title: "synaptic wants to remove everything?!?!"
date: 2006-05-27
forum: General Help
---

### Post by iamsobored0056 on 2006-05-27
hi, a few days ago i tried to install gnomad2 and there were some depency problems so i gave up.  now for some reason whenever i want to install something on the terminal it says this: 
> Reading package lists... Done
Building dependency tree... Done
lm-sensors is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnomad2: Depends: libglib2.0-0 (>= 2.10.0) but 2.8.3-0ubuntu1 is to be installed
           Depends: libpango1.0-0 (>= 1.12.0) but 1.10.1-0ubuntu1 is to be installed
           Depends: libusb-0.1-4 (>= 2:0.1.11) but 2:0.1.10a-17ubuntu1 is to be installed
           Depends: libxrender1 (>= 1:0.9.0.2) but 1:0.9.0-1 is to be installed
  libcairo2: Depends: libc6 (>= 2.3.6-6) but 2.3.5-1ubuntu12 is to be installed
  libcairo2-dev: Depends: libcairo2 (= 1.0.2-0ubuntu1) but 1.0.4-2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

also, if i want to do anything in synaptic, it will try to remove a few hundred programs on my computer.  im still pretty new to ubuntu and im completley lost on what to do.  please help!](*,)

---

### Post by 3rdalbum on 2006-05-27
I installed gnomad2 just now to test it out. There were no problems.

Have you tried running:
```
sudo apt-get update
```?

The repositories are behaving a little strangely at the moment, probably due to the impending release of Ubuntu 6.06. That might be the cause of your problem.

If updating the package list doesn't help, try doing what it suggests: sudo apt-get -f install.

Also, if you have any 3rd-party repositories in your sources.list, try getting rid of them.

---

