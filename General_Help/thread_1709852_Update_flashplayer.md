---
title: "Update flashplayer"
date: 2011-03-18
forum: General Help
---

### Post by thenickrulz on 2011-03-18
How do i update flash player for chromium????? can someone please help!!!!!!!!!!!!!:P:(:icon_frown::icon_frown::icon_frown::icon_frown::icon_frown::icon_

---

### Post by pqwoerituytrueiwoq on 2011-03-18
it should use it if it is setup for firefox
you can do in manually
sudo mkdir /opt/google/chrome/plugins
sudo mv Downloads/libflashplayer.so  /opt/google/chrome/plugins
if you have 64bit get it here [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)
otherwise get it on the main adobe page .tar.gz or .bz2 what ever it has i forget

---

### Post by thenickrulz on 2011-03-18
I have downloaded it from the website but how do i install it???:o

---

### Post by pqwoerituytrueiwoq on 2011-03-18
as i posted above 
make place to install to
sudo mkdir /opt/google/chrome/plugins
install flash to chrome
sudo mv Downloads/libflashplayer.so  /opt/google/chrome/plugins

BTW extract the file to your downloads folder 1st

---

### Post by thenickrulz on 2011-03-18
still won't work.. can you explain better i am a total n00b

---

### Post by thenickrulz on 2011-03-18
PLEASE
The only reason i want to do this is because is says get the new version of flashplayer on every site i go to it is irritating...!

---

### Post by usatonycuba on 2011-03-19
> **thenickrulz said:**
> still won't work.. can you explain better i am a total n00b

[QUOTE=pqwoerituytrueiwoq]
as i posted above 
make place to install to
sudo mkdir /opt/google/chrome/plugins
install flash to chrome
sudo mv Downloads/libflashplayer.so /opt/google/chrome/plugins

BTW extract the file to your downloads folder 1st
[/QUOTE]
Better explanation than that one ? :confused: It was clear like crystal.

Any way.. 
1) Download plugins (to your local Download folder) that depends in your browser.
2) Extract the file to your downloads folder first (Use extrat here option from your Mouse right Click)
3) Open your Ubuntu *TERMINAL* and type *[COLOR="Sienna"]sudo su[/COLOR]*, enter your passsword
4) In the same *TERMINAL* type *[COLOR="Sienna"]sudo mkdir /opt/google/chrome/plugins[/COLOR]* <--as pqwoerituytrueiwoq said **make place to install**
5) In the same *TERMINAL* window type *[COLOR="Sienna"]sudo mv Downloads/libflashplayer.so /opt/google/chrome/plugins[/COLOR]*  <-- Where *[COLOR="Sienna"]Downloads[/COLOR]* is ( your local Download folder) as mention before.

---

### Post by lovinglinux on 2011-03-19
Get Flash-Aid. It only works in Firefox, but the plugin installed by it will be detected by Chromium as well.

[http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)

---

### Post by thenickrulz on 2011-03-19
2) Extract the file to your downloads folder first (Use extrat here option from your Mouse right Clic cant do this step....... ](*,)](*,)](*,)
getting this...

 cannot create directory `/opt/google/chrome/plugins': No such file or directory

---

### Post by usatonycuba on 2011-03-19
> **thenickrulz said:**
> 2) Extract the file to your downloads folder first (Use extrat here option from your Mouse right Clic cant do this step....... ](*,)](*,)](*,)
getting this...

 cannot create directory `/opt/google/chrome/plugins': No such file or directory

Sorry, I do not follow you ... 

Step 2) has nothing to do with creating a new directory dude (that will be Step 3).

 2) Refers to download "file-x" (by "x" means any name) , unpack it into the desired folder (which is the folder where you downloaded the file-x from your browser), then using the right click option from your mouse  chose the option to *extract here* .. will decompress the file-x in the same folder, creating a new folder and/or decompressing files in the file that had the original file-x..

I think if you're not sure of the files you extracted, you must copy the downloaded file to a new place, unpack it, and you see the result, I mean .. see the files It has it inside before unpacked.

If you have problems creating a directory, and your are not sure were is locate your Google Chrome, noob way to see it: Go to Aplications -> Internet -> Right Click on Chrome icon (and select add to launcer panel) -> (In your panel bar) right Click on Chrome icon and select Properties .. and take a look at Command box, it show where is Instaled.. is something like this --> /opt/google/chrome/google-chrome.

So from there, you have  an idea were your NEW-DIR will be place at.. as was said in Step 4) and 5)

---

### Post by lovinglinux on 2011-03-19
> **thenickrulz said:**
> 2) Extract the file to your downloads folder first (Use extrat here option from your Mouse right Clic cant do this step....... ](*,)](*,)](*,)
getting this...

 cannot create directory `/opt/google/chrome/plugins': No such file or directory

As I said, get Flash-Aid, install it via Firefox, run it and it will generate the necessary commands to get the latest beta flash and remove conflicting plugins, then execute the commands for you. Chromium will detect the plugin installed by it.

BTW, it seems you have Chromium and "usatonycuba" is giving instructions for Chrome.

---

### Post by thenickrulz on 2011-03-19
cool but how do i know if i did it right and it is installed??
cool i think it worked... but do u mean i have to use firefox now????

---

### Post by pqwoerituytrueiwoq on 2011-03-19
[http://www.adobe.com/swf/software/flash/about/flashAbout_info_small.swf](http://www.adobe.com/swf/software/flash/about/flashAbout_info_small.swf)
that will tell you what version of flash you have
Since firefox is the default browser on so many linux distros chrome will look for flash where it would be used by firefox
i have used /opt/google/chrome/plugins so i could have 2 different versions of flash installed at once 
at one point latest flash would not work on a game i played
but the working flash had no sound
it was basically pick your bug
so i had 1 flash in chrome for the game 
and another flash in firefox

---

### Post by lovinglinux on 2011-03-19
> **thenickrulz said:**
> cool but how do i know if i did it right and it is installed??
cool i think it worked... but do u mean i have to use firefox now????

If the extension executed the commands in a terminal all through the end without serious errors and you get a message saying that you can close the terminal, then you are good.

You can check the installed version typing **about[noparse]:[/noparse]plugins** in Firefox, Chrome, Chromium or Opera.

You don't need to use Firefox now. Although the extension is designed for Firefox, it installs flash in the default system location, which is recognized by all major browsers.

---

### Post by thenickrulz on 2011-03-19
Yes it worked.
Can i update my firefox???

---

### Post by lovinglinux on 2011-03-19
> **thenickrulz said:**
> Yes it worked.
Can i update my firefox???

Go to "System >> Administration >> Update Manager" in the main Ubuntu menu.

---

### Post by thenickrulz on 2011-03-19
But it isant a package so how do i get it???:confused:

---

### Post by pqwoerituytrueiwoq on 2011-03-19
if you want firefox 4 i made a simple script to install it
[http://ubuntuforums.org/showthread.php?p=10579081](http://ubuntuforums.org/showthread.php?p=10579081)

---

### Post by thenickrulz on 2011-03-19
so can i copy it into the termainal or do i have to write it in????
And also does it work on 10.10????

---

### Post by pqwoerituytrueiwoq on 2011-03-19
you can download it at the end of the post it is a shell script
if you want to copy/paste open gedit up and paste it there save it 
anywhere with any name 
then run it from the terminal with sh /path/to/myfile
obviously change /path/to to the actual path to
will work on any i686 or x86_64 linux install
uname -m will tell you 
BTW ubuntu is only offerend in i686 and x86_64

---

### Post by thenickrulz on 2011-03-19
ok COOL THANKS

---

### Post by thenickrulz on 2011-03-20
got it from this site [http://news.softpedia.com/news/How-to-Install-Firefox-4-in-Ubuntu-10-10-10-04-9-10-and-9-04-183595.shtml](http://news.softpedia.com/news/How-to-Install-Firefox-4-in-Ubuntu-10-10-10-04-9-10-and-9-04-183595.shtml)
can i still upgrade to 11.4 when it comes out with this version of firefox...

---

### Post by pqwoerituytrueiwoq on 2011-03-20
you can the way i made it is risk free it does not affect anything but itself

---

### Post by usatonycuba on 2011-03-23
> **lovinglinux said:**
> 

BTW, it seems you have Chromium and "usatonycuba" is giving instructions for Chrome.

> **thenickrulz said:**
> How do i update flash player for chromium????? can someone please help!!!!!!!!!!!!!:P:(:icon_frown::icon_frown::icon_frown::icon_frown::icon_frown::icon_](*,) My bad, good catch lovinglinux ;)

---

### Post by thenickrulz on 2011-04-13
just got firefox 4 and i am using flah-aid... wrks well..

---

### Post by sg1efc on 2011-04-28
> **lovinglinux said:**
> Get Flash-Aid. It only works in Firefox, but the plugin installed by it will be detected by Chromium as well.

[http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)

Holy crap! Every time I have done an upgrade to Ubuntu 64bit or FireFox 64bit version, I always had Flash Player problems. Just upgraded to Ubuntu 11.04 and sure enough Flash was not working again in FireFox.

Just found this post and tried this plugin & it worked great! Thank you very much LovingLinux and Thanks a lot to the creator of this plugin.  :)

---

### Post by lovinglinux on 2011-04-28
> **sg1efc said:**
> Holy crap! Every time I have done an upgrade to Ubuntu 64bit or FireFox 64bit version, I always had Flash Player problems. Just upgraded to Ubuntu 11.04 and sure enough Flash was not working again in FireFox.

Just found this post and tried this plugin & it worked great! Thank you very much LovingLinux and Thanks a lot to the creator of this plugin.  :)

You are welcome. BTW, I am the developer of the extension :-)

---

### Post by rburkartjo on 2011-04-28
loving another thanks again for creating the flash aid ff plugin works great in natty

---

### Post by lovinglinux on 2011-04-28
> **rburkartjo said:**
> loving another thanks again for creating the flash aid ff plugin works great in natty

You are welcome. I am also using natty and is working great too.

Cheers

---

### Post by sg1efc on 2011-04-28
> **lovinglinux said:**
> BTW, I am the developer of the extension :-)

Cool!  :)  Wish I had even 1% of your computer knowledge.    Thanks again.    :smile:

---

