---
title: "Kubuntu 9.04 Questions"
date: 2009-09-09
forum: General Help
---

### Post by o_swas on 2009-09-09
Hello,

I just installed Kubuntu 9.04 in Parallels 4 for Mac.  I also use Kubuntu 7.10 but have never used Kubuntu with KDE 4.  I have some (hopefully) simple questions that I need answered so I can start using Kubuntu 9.04:

1.  I'm behind a corporate firewall the requires authentication.  In Kubuntu, I went to "Network Settings - System Settings" and chose "Manually specify the proxy settings" and entered the proxy URL.  However, in the "Authorization" section, I want to specify the username and password, but those options are disabled -- only "Prompt as needed" is available for selection.  How can I enter the proxy username and password?  I've never been prompted, even when I told the system to update the date/time automatically, which I assume it needs to get from the internet.

2.  Where is Synaptic and/or Aptitude?  Under Applications --> System I see something called KPackageIt, but I don't see Synaptic anywhere.  KPackageIt doesn't seem to be picking up the proxy settings either as it never prompts me for the username/password.

That should be enough to get me going.  Thank you!!!!!

---

### Post by gastly on 2009-09-09
I dunno about the first, but you can install Synaptic with this command:
```
sudo apt-get install synaptic
```
And as for **aptitude**, it's installed by default in all the Ubuntu versions and since it's a command-line program you will need to run it from the terminal, just type **aptitude** in a terminal :)

---

### Post by ashwinhgtx on 2009-09-09
Doesn't KPackageIt have its own proxy preferences? I'm not on KDE4 right now, so I'm not very sure.

---

### Post by ashwinhgtx on 2009-09-09
> **gastly said:**
> I dunno about the first, but you can install Synaptic with this command:
```
sudo apt-get install synaptic
```
And as for **aptitude**, it's installed by default in all the Ubuntu versions and since it's a command-line program you will need to run it from the terminal, just type **aptitude** in a terminal :)

I don't think that would work as he is behind a proxy. He'll have to edit the bash.bashrc file in /etc and put in the proxy values there.

---

### Post by gastly on 2009-09-09
> **ashwinhgtx said:**
> I don't think that would work as he is behind a proxy. He'll have to edit the bash.bashrc file in /etc and put in the proxy values there.
Oops, forgot about that.

**o_swas**:
You can configure apt to use proxy settings this way:

```

export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/

```

You can add it to your ~/.bashrc file to preserve the changes.

---

### Post by o_swas on 2009-09-09
> **ashwinhgtx said:**
> Doesn't KPackageIt have its own proxy preferences? I'm not on KDE4 right now, so I'm not very sure.

From what I can tell, KPackageIt does not have its own proxy settings.

---

### Post by o_swas on 2009-09-09
> **gastly said:**
> Oops, forgot about that.

**o_swas**:
You can configure apt to use proxy settings this way:

```

export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/

```

You can add it to your ~/.bashrc file to preserve the changes.

Thanks gastly, I'll try that if all else fails.  If possible I'd rather do everything through the GUI, which is why I'm wondering why I can't set the proxy authorization through the GUI.  It's clearly there, but for some reason its disabled.

---

