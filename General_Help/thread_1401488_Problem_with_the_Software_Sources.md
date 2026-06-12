---
title: "Problem with the Software Sources"
date: 2010-02-08
forum: General Help
---

### Post by yeketaz on 2010-02-08
Hi To All problem offhand ... I Summary I
When the Software Sources Load  do with the My Internet message I connected
```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```And then message
```
E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
E: Unable to lock the list directory
```And then message
```
E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```Terminal time with you this error
```
E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
```When the updates with this message
```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list, E:The list of sources could not be read.'
```Did problem Please help me

---

### Post by wojox on 2010-02-08
Go yo /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list and post what's in there back up here and lets take a look.

---

### Post by shriramrs31 on 2010-02-08
> **yeketaz said:**
> Hi To All problem offhand ... I Summary I
When the Software Sources Load  do with the My Internet message I connected
Did problem Please help me

Are you running the program as root ?

Please try "sudo apt-get update" in terminal and see if it works. If not please paste the error message here.

And also please check if your internet connection is properly configured. Sometimes internet access via a proxy with authentication requires extra setup.

Hope this helps.

---

### Post by yeketaz on 2010-02-08
> **wojox said:**
> Go yo /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list and post what's in there back up here and lets take a look.
I went to send her files&#1567;

---

### Post by yeketaz on 2010-02-08
> **shriramrs31 said:**
> Are you running the program as root ?

Please try "sudo apt-get update" in terminal and see if it works. If not please paste the error message here.

And also please check if your internet connection is properly configured. Sometimes internet access via a proxy with authentication requires extra setup.

Hope this helps.
I have root access and have connection time is right

---

### Post by yeketaz on 2010-02-08
> **wojox said:**
> Go yo /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list and post what's in there back up here and lets take a look.
Content of said path
```
n
```

---

### Post by yeketaz on 2010-02-08
> **wojox said:**
> Go yo /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list and post what's in there back up here and lets take a look.

```
http://www.4shared.com/file/217432617/6d49e9b/ubuntu-wine-ppa-karmic.html

```

---

### Post by 3rdalbum on 2010-02-08
Remove that file. All lines in your repository entries (sources.list or *.list) must begin with "deb", "deb-src" or the hash symbol #).

---

### Post by wojox on 2010-02-08
If you want to download wine install it from Synaptic Package Manager or use this site: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) . Stay away from weird file sharing sites like that.

---

### Post by yeketaz on 2010-02-08
> **wojox said:**
> If you want to download wine install it from Synaptic Package Manager or use this site: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) . Stay away from weird file sharing sites like that.
When I installed &#1612;Wine, the following warnings was faced with sham. Help me[IMG]http://www.google.com/images/cleardot.gif[/IMG]
```
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

---

