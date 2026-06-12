---
title: "HOWTO: Hamchi remote desktop with vinagre"
date: 2009-06-25
forum: General Help
---

### Post by devfolarin on 2009-06-25
Hello fellow Linux followers!

[SIZE=6]HOWTO:RemoteDesktop +Hamachi[/SIZE]

[SIZE=3]**1.**installing hamachi[/SIZE]:

[https://secure.logmein.com/products/hamachi/list.asp](https://secure.logmein.com/products/hamachi/list.asp)

use the link and download the linux tarball.gz.

once you download the tarball extract it by right clicking the file then extracting it here.

once its finished extracting cd to the directory you extracted it from.

EX.

```

cd Desktop
cd hamachi-0.9.9.9-20-lnx

```--------------------------------------------------------------------------------------------------------

then type : ```
sudo make install
```and click enter.

then type : ```
sudo /sbin/tuncfg
```and click enter.

there you go!!! you should have succesfully installed hamachi!

now to run hamachi!

```

hamachi-init

hamachi start

hamachi login

hamachi set-nick (what ever nick name you want)


```now that your loged in run the same on your other os 
[its easy if its windows]

you now need to either create or login into a network

```

#to create

hamachi create (name of network) (password if any)

#to join

hamachi join (name of network) (password if any)


```lets say your joining a network

once you join you must go online in the network

```

hamachi go-online (name of network)

#you can join multiple networks

```now that your online in the network open up a console and type ```
 vinagre 
```a window will come up after a little while .

click the connect button.

go back to the other console or open up another one and type ```
hamachi list
```type the hamachi ip of the computer you would like to connect to and it should work presto!

################################################################################
notes.

you have to have a vnc server running on the computer you wish to view

on windows get real vnc free edition -> [http://www.realvnc.com/products/free/4.1/download.html](http://www.realvnc.com/products/free/4.1/download.html)

on ubuntu just go to system-> prefrences-> remote desktop-> allow others to view desktop, allow others to control desktop * i recomend you set a password.

on osx i think you just enable remote desktop

Thank you for reading 

comment if anything was unclear or if you would like me to add something!

Devfolarin OUT:popcorn:

---

