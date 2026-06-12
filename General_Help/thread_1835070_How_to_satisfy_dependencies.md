---
title: "How to satisfy dependencies"
date: 2011-08-28
forum: General Help
---

### Post by vinayy on 2011-08-28
I have installed Ubuntu 10.10 in my laptop.I also configure it for day to day use.But there is one problem into it.I install the packages which requires to sharing the data with windows on other computers.But there are some dependenecies are come with it.The dependencies are shows into Synaptic Package Manager.When i tried to remove it it shows many of packages must to remove like vlc ,kde-desktop...etc..And there also no any upgrade option or re-install option on it.When i tried to remove it it shows many of dependencies are present can't remove.So please help me.

Thanking You...

---

### Post by ajgreeny on 2011-08-28
Are you saying you have already installed the sharing packages and are now trying to remove their dependencies?  Why do you want to remove them?

If you are trying to do that, I am afraid it is not possible.  You could use synaptic and try again after deselecting  "Consider recommended packages as dependencies" in synaptic preferences, but that may make no difference in your particular case;  it depends on the specific packages you are dealing with.

---

### Post by snowpine on 2011-08-28
If Package A depends on Package B, then you can't remove B without also removing A. That is the meaning of the word "dependency." Package B provides some functionality that Package A also requires. Unless you are running out of hard drive space, this is nothing to worry about.

If you have questions about a particular package (or packages) then please be specific and I'll try my best to help. :)

---

