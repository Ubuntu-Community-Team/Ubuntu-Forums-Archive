---
title: "How to Install PHPmotion on Ubuntu Server 9.10"
date: 2009-11-20
forum: General Help
---

### Post by kadeous on 2009-11-20
Greetings All! I'm in no way very knowledgeable when it comes to linux, but my first project was to setup a website running PHPmotion. I've done a lot of trial and error and learned how to navigate around them. Please keep in mind that I'm not responsible for anything that may happen to your server/system. I'm just listing out how I installed the server.
 
I followed the directions at [http://www.howtoforge.com/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2) However I didn't install ISPConfig as it was too complicated for me atm to understand so much at once, I did use webmin to get everything running how I wanted it. Also, he uses LVM and from what I gather it allows for multiple websites, I again am only doing 1 website for myself so it's up to you.
 
Now after doing that I went over to [http://linux.justinhartman.com/FFmpeg,_FFmpeg-PHP,_Lame,_Libogg,_Libvorbis,_FLVtool2,_Mplayer,_Mencoder,_AMR_Installation#Install_libvorbis](http://linux.justinhartman.com/FFmpeg,_FFmpeg-PHP,_Lame,_Libogg,_Libvorbis,_FLVtool2,_Mplayer,_Mencoder,_AMR_Installation#Install_libvorbis) 
I followed all the instructions and replaced version numbers with newer ones.
 
After I setup that I uploaded phpmotion to my server using FTP, yeah I know I could have created a Samba share and just zipped it over but I wanted to learn how to use FTP and setup FTP on my server.
 
Make sure you do everything here or you will have errors: [http://wiki.phpmotion.com/InstallingV3](http://wiki.phpmotion.com/InstallingV3)
 
Next you will have to [http://phpmotion.com/content/view/16/32/](http://phpmotion.com/content/view/16/32/) make sure you edit your php.ini file, just search for the variables and change thier values to the required value.
 
Now I went into myphpadmin to make a new database and user. This is up to you and you can name it anything and make a user named whatever. But it's important to do this first. Write down the information so you can enter it later into the setup.
 
Before you go further also make sure that you edit the Apache2 Directives to AllowOveride All or the rewrite feature will not work. [http://httpd.apache.org/docs/2.0/mod/directives.html](http://httpd.apache.org/docs/2.0/mod/directives.html) just click the AllowOveride link and read about it, just a note that I used webmin to edit the directive, outside of that I have no clue how you do it.
 
Now what you'll want to do is open up [http://myipaddress/setup/](http://myipaddress/setup/) 
Just do everything the setup tells you to do, it's rather linear and easy to follow. After installation you'll be prompted to delete your setup directory so just do that and click login.
 
The issue I was now faced with, Captcha image wouldn't display.
 
To solve the Captcha issues I had to move the font under the includes folder to the system font folder and re-load the sytem fonts. The font is called DoradoHeadline.ttf btw. Path to the system font /usr/share/fonts/truetype just place it in that folder. Then all you have to do is type:
 
sudo fc-cache -f -v
 
I hope this helps someone around here in the Ubuntu Community, it was a fun learning experience for me. So far I've been using Ubuntu for 1 week and I'm enjoying every last bit of it.
 
Everything works as needed some movies will not convert to FLV because of how they were encoded, I'm still working on this issue.
 
Cheers!

---

### Post by cmacleod on 2010-03-25
> **kadeous said:**
> 
 
The issue I was now faced with, Captcha image wouldn't display.
 
To solve the Captcha issues I had to move the font under the includes folder to the system font folder and re-load the sytem fonts. The font is called DoradoHeadline.ttf btw. Path to the system font /usr/share/fonts/truetype just place it in that folder. Then all you have to do is type:
 
sudo fc-cache -f -v
 
I hope this helps someone around here in the Ubuntu Community, it was a fun learning experience for me. So far I've been using Ubuntu for 1 week and I'm enjoying every last bit of it.
 
Everything works as needed some movies will not convert to FLV because of how they were encoded, I'm still working on this issue.
 
Cheers!

Like many others who were trying to install phpmotion on a new ubuntu server I experienced the same problem.  After many searches looking for possible other missing packages, searching the phpmotion forum.  My google searches found your article.  Thanks,  this missing last part quoted above.  Brought my second evening of frustration to an end on my newly built server.

I have now successfully got the captcha graphics appearing and now I'm onto sorting other issues.  So feel free to post the rest of your solutions too.  I'm the next one now!  something to do with uu_upload.pl ?!?

Many thanks!

Colin

---

### Post by alighouston on 2010-06-03
i almost installed the whole thing on a home server final step was to setup the cron job to convert the files and php was not working with me lol and it messes up every thing when i followed some instructions from a random stupid post just be careful as the hosts who are offering install service will post stuff that you should not do and instead of helping you they will say stuff like just host it with us.
Well for uu_upload.pl its a pl script which should be handled by you CGI if its giving you a download then your virtual host is missing pl execution code and its treating it as a text file.
If its giving you some other error like permission denied then have to change permission to 775.
i will keep you guys posted how this will further go.
My reason to install it is to host new movies at lan so i don't have 5 people downloading the same movie at my home to watch and eat up all my bandwidth lol its for a good cause "my cause"

---

### Post by teddy939 on 2011-04-18
i have problem installing phpmotion in ubuntu server 9.10 and end up using  cenos 5.5 and clipshare.. tq for the info
my website [http://www.1tube.my/](http://www.1tube.my/)

---

### Post by short_tounge on 2011-04-28
hi,i also have been working on to use phpmotion on my Ubuntu 10.10 . 
and the i get stuck by the "blank page" on phpmotion installation setup.
so,after doing some research.the culprit maybe of the files that need to be uploaded to ftp server in binary mode as you explain here.
"
After I setup that I uploaded phpmotion to my server using FTP, yeah I  know I could have created a Samba share and just zipped it over but I  wanted to learn how to use FTP and setup FTP on my server."

so,could u please explain little detail how did u upload the selected files in binary mode and ascii mode? what type of ftp server u using? n i assume that after upload it to ftp server,then i download it and put it at /var/www right? correct me if im wrong please. (i have install webmin with vsftpd modules but still dont know how to upload and download files.sigh)

tq

---

