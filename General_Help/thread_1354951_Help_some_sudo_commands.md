---
title: "Help some sudo commands"
date: 2009-12-14
forum: General Help
---

### Post by JoeDaFlow on 2009-12-14
Hello guys, i need some help with the terminal command to install some programs.
I need mysql 5.1, navicat, and java. 
P.S if there is any list witch contains all the commands please refer it.
Thank you ;P
-JoeDaFlow

---

### Post by Physical Hook on 2009-12-14
```
sudo apt-get install mysql-server
sudo apt-get install sun-java6-jre sun-java6-plugin

```

Not sure about navicat so I'll leave it as a question to someone else.

---

### Post by nothingspecial on 2009-12-14
> **JoeDaFlow said:**
> Hello guys, i need some help with the terminal command to install some programs.
I need mysql 5.1, navicat, and java. 
P.S if there is any list witch contains all the commands please refer it.
Thank you ;P
-JoeDaFlow

To search for packages in the terminal ```
apt-cache search package
``` trouble is this will search through the description aswell and may print out 100s of packages. So if you know the rough name of the package (maybe not the version number eg) you can use the -n flag that just prints out package whose name matches your search. For example, for your request

```
apt-cache search -n mysql
```

find the one you want then ```
sudo apt-get install package
```

---

### Post by Cope57 on 2009-12-14
Since you are wanting to install Navicat, I am assuming you purchased the application, if you are installing the free Navicat Lite Tar version of navicat in KDE/GNOME environment, you can extract the tar file to anywhere. The command is for example: **tar -zxvf navicat8_lite_en.tar.gz** . To start Navicat, you can use the command **./start_navicat**.

You can locate Navcat at the [Navicat Download Center]("http://www.navicat.com/en/download/download.html")

---

### Post by JoeDaFlow on 2009-12-14
> **Cope57 said:**
> Since you are wanting to install Navicat, I am assuming you purchased the application, if you are installing the free Navicat Lite Tar version of navicat in KDE/GNOME environment, you can extract the tar file to anywhere. The command is for example: **tar -zxvf navicat8_lite_en.tar.gz** . To start Navicat, you can use the command **./start_navicat**.

You can locate Navcat at the [Navicat Download Center]("http://www.navicat.com/en/download/download.html")

Well there is an patcher in window, you think it works here too?;P

---

