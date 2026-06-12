---
title: "Installing GIMP 2.8"
date: 2012-05-09
forum: General Help
---

### Post by Philip Gray on 2012-05-09
Good evening 
 
I have no experience installing software from the terminal. I am having difficulties compiling and installing GIMP 2.8 in 10.04. I downloaded the tz compressed file from the GIMP website. I extracted it and read the readme file. The file said I must run 'make' and then 'make install'. All I received were error messages. I then did a search on google on how to install software from the terminal. I found this site [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html). 
 
I executed ./configure as per the above page. The response advised that it required the babl >= 0.1.10. I downloaded this package from softpedia. I unpacked the package and ran the ./configure commands. All I received were error messages. I then did a search on google for help on how to install GIMP 2.8. I found this page on how to install it in 12.04 ([http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu](http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu)). I followed it was able to install the babl package ( './autogen.sh--prefix/opt/gimp-2.8', 'make -j5' and 'make install -j5'). When I ran ./configure --prefix=/opt/gimp-2.8 in my gimp-2.8.0 temp folder I was advised that I needed the gegl package. I downloaded it. After then after having done this and when I tried to install with the ./configure --prefix=/opt/gimp-2.8 command. I was advised that I needed  the GLIB package. I downloaded it and unpacked it. I then ran the './configure --prefix=/opt/gimp-2.8', 'make -j5' and 'make install -j5'. After having done this I went back into my gegl folder and ran the './configure --prefix=/opt/gimp-2.8' I received the error message again that I need the GLIB package. What must I do to sort this out? 
 
Any help will be appreciated. I have attached the gegl and glib responses. 
 
Regards 
Philip

---

### Post by idoitprone on 2012-05-09
> **Philip Gray said:**
> Good evening 
 
I have no experience installing software from the terminal. I am having difficulties compiling and installing GIMP 2.8 in 10.04. I downloaded the tz compressed file from the GIMP website. I extracted it and read the readme file. The file said I must run 'make' and then 'make install'. All I received were error messages. I then did a search on google on how to install software from the terminal. I found this site [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html). 
 
I executed ./configure as per the above page. The response advised that it required the babl >= 0.1.10. I downloaded this package from softpedia. I unpacked the package and ran the ./configure commands. All I received were error messages. I then did a search on google for help on how to install GIMP 2.8. I found this page on how to install it in 12.04 ([http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu](http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu)). I followed it was able to install the babl package ( './autogen.sh--prefix/opt/gimp-2.8', 'make -j5' and 'make install -j5'). When I ran ./configure --prefix=/opt/gimp-2.8 in my gimp-2.8.0 temp folder I was advised that I needed the gegl package. I downloaded it. After then after having done this and when I tried to install with the ./configure --prefix=/opt/gimp-2.8 command. I was advised that I needed  the GLIB package. I downloaded it and unpacked it. I then ran the './configure --prefix=/opt/gimp-2.8', 'make -j5' and 'make install -j5'. After having done this I went back into my gegl folder and ran the './configure --prefix=/opt/gimp-2.8' I received the error message again that I need the GLIB package. What must I do to sort this out? 
 
Any help will be appreciated. I have attached the gegl and glib responses. 
 
Regards 
Philip

too much effort
do yourself a favor

NOTE: be careful with rm -r
rm -r gimp-src
no make 
no compile

just do these commands

```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp 

sudo apt-get update
sudo apt-get install gimp
```

[http://iloveubuntu.net/gimp-28-officially-released-gimp-28-final-ppa-available](http://iloveubuntu.net/gimp-28-officially-released-gimp-28-final-ppa-available)

---

### Post by Philip Gray on 2012-05-09
Hi idoitprone

Tks for yr help.

Regards
Philip

(\ /)
(O.o)
(> <)

---

### Post by jochen-02 on 2012-05-12
> **idoitprone said:**
> just do these commands

```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp 

sudo apt-get update
sudo apt-get install gimp
```[http://iloveubuntu.net/gimp-28-officially-released-gimp-28-final-ppa-available](http://iloveubuntu.net/gimp-28-officially-released-gimp-28-final-ppa-available)Did you read the version information? 
> Ubuntu 10.04 Lucid LynxThe repository provides just Oneiric Ocelot (11.10) and Precise Pangolin (12.04).

---

### Post by Enigmapond on 2012-05-12
Unfortunately, as of now, there is no easy way to install GIMP 2.8 in Lucid. Mainly because GIMP 2.8 depends on many new underlying libraries which can't be found in the repositories of those older Ubuntu versions. Thus, you would first need to compile those libraries and then go for compiling GIMP itself, and that would obviously require a lot of work.

---

### Post by idoitprone on 2012-05-12
> **jochen-02 said:**
> Did you read the version information? 
The repository provides just Oneiric Ocelot (11.10) and Precise Pangolin (12.04).

some people are lazy at updating their info. Heck I would. I probably have account that says  that I am still in elementary when I already graduated high school

---

### Post by shreepads on 2012-05-18
> **Enigmapond said:**
> Unfortunately, as of now, there is no easy way to install GIMP 2.8 in Lucid. Mainly because GIMP 2.8 depends on many new underlying libraries which can't be found in the repositories of those older Ubuntu versions. Thus, you would first need to compile those libraries and then go for compiling GIMP itself, and that would obviously require a lot of work.

Well it's sure not easy, but I've just created this post, which may help: [How to use GIMP 2.8 on Lucid 10.04.4 LTS ]("http://ubuntuforums.org/showthread.php?t=1982183")

---

