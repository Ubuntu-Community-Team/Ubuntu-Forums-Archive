---
title: "Unable to see java applets in browser"
date: 2012-04-03
forum: General Help
---

### Post by p3aul on 2012-04-03
Ubuntu 10.4 Firefox 9.0.1

I cannot see java applets in Firefox or Chrome. When I click on the link  the page gives me to install java, it invariably fails, every time. I  try to install manually. I become root, I click on permissions and  choose "Allow executing file as program". I click on the file and it  tries to open it in gedit. I already have Java installed anyway. its in  the etc folder under File System.
Thanks,
Paul

---

### Post by na5h on 2012-04-03
Are you using OpenJDK Java or Oracle Java?

Some commercial applications tend not to work too well with OpenJDK. Oracle Java is no longer available in the repositories, but you can still download and install it manually from [Oracle]("http://www.oracle.com/technetwork/java/javase/downloads/index.html").

Oracle Java can also be installed from a repository.
If you want to use Oracle Java, this is the code for removing OpenJDK and installing the Oracle JDK:
```
sudo apt-get purge openjdk*
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```
Please note that the repository above provides the full Oracle JDK7 package, you can't only install Oracle JRE using this repository!

If you want to use OpenJDK, it can be found in the Software Center.

You can use [this page]("http://www.java.com/en/download/testjava.jsp") to check whether Java is working on your computer or not.

If you don't want to use Oracle Java anymore, just run this code:
```
sudo apt-get remove oracle-java7-installer
```

---

### Post by dniMretsaM on 2012-04-03
Install the IcedTea plugin. I think the package name is [FONT=Courier New]icedtea6-plugin[/FONT].

---

### Post by p3aul on 2012-04-05
Thanks for replying! I see no need for the OpenJDK or Icedtea plugin. I tried that route but couldn't get them to work! If I'm not mistaken, Java was originally made for linux, not windows, anyway. I see no need for OpenJDK. Anyway na5h, I ran the first command in your post and discovered I didn't have OpenJDK installed anyway. The other commands worked great and I now can see java applets! Don't really care for them I'd rather have  flash. But I hate to not see a website as it was designed to be seen. So, thanks for your help! ):P

---

