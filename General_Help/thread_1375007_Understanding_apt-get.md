---
title: "Understanding apt-get"
date: 2010-01-07
forum: General Help
---

### Post by eric_1982 on 2010-01-07
I need help so I can help myself more. I am hoping some one can help me understand a few things about the Apt-Get command. 

**Where can I find what packages are available for the use of apt-get?**

When I am trying to learn to install something I will search articles on the web. They will tell me to a apt-get command to pull some library or install a file. I come across an error saying the package can not be found or it has been moved. After doing some more searching I will find some updated article that has the new updated package name in the sudo command.

[I]Example: sudo apt-get install libapache-mod-ssl

Error: This may mean that the package is missing, has been obsoleted, or is only available from another source[/I]

I have looked at my /etc/apt/sources.list file and have followed the URL path and looked around on some of the sites. The part that confuses me is **how do I know what sytx to enter?**

If some one could please help explain this a little more to me or point me to some information that can help me be a little more reliant on myself then other articles it would be greatly appreciated. Thanks!

---

### Post by snowpine on 2010-01-07
You can use 'apt-cache search' for example:

```
sudo apt-cache search firefox
```

A lot of users find the Synaptic Package Manager is a really easy way to search the available packages.

I would advise you to be wary of following random tutorials on the web. If you need help with something, first check the **official** Ubuntu documentation and wiki, then ask for advice here on the forums. If you are following some random internet tutorial, make sure that a) you trust the person writing it; and b) it is specific to your release of Ubuntu (tutorials for older versions might not work with the current).

---

### Post by eric_1982 on 2010-01-07
I prefer not to install the gui (x) on my server, so that's why I try to do it all with bash. I am wondering how others find what packages and applications are available to install using the apt-get install command.

Can I run Synaptic Package Manager from bash?

Does any one know any good articles on the apt-get commands and finding the right packages and applications sytx. How do others find these?

---

### Post by philinux on 2010-01-07
```
apt-cache policy libapache-mod-ssl
```

Gives.

libapache-mod-ssl:
  Installed: (none)
  Candidate: (none)
  Version table:

In other words it don't exist in the ubuntu repos.

---

### Post by snowpine on 2010-01-07
Well, like I said, 'apt-cache search' is one good way. You can also try 'man apt' or browse the available packages at [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by mcduck on 2010-01-07
> **snowpine said:**
> You can use 'apt-cache search' for example:

```
sudo apt-cache search firefox
```

A lot of users find the Synaptic Package Manager is a really easy way to search the available packages.

I would advise you to be wary of following random tutorials on the web. If you need help with something, first check the **official** Ubuntu documentation and wiki, then ask for advice here on the forums. If you are following some random internet tutorial, make sure that a) you trust the person writing it; and b) it is specific to your release of Ubuntu (tutorials for older versions might not work with the current).

apt-cache doesn't require root privileges, so no "sudo" needed for this.. ;)

---

### Post by snowpine on 2010-01-07
> **mcduck said:**
> apt-cache doesn't require root privileges, so no "sudo" needed for this.. ;)

Thanks for the correction, it's been a little while since I used that command. :)

---

### Post by eric_1982 on 2010-01-07
Thanks Snowpine I missed the apt-cache search command the first time I read your reply. That is exactly what I was looking for. Thanks again!

---

