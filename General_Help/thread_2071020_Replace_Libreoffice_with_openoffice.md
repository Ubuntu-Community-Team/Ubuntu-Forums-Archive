---
title: "Replace Libreoffice with openoffice"
date: 2012-10-14
forum: General Help
---

### Post by aabed91 on 2012-10-14
Hi all,

When i use openoffice i found it better than libreoffice 
So i search to download it and remove libreoffce

The way is very easy:
First: remove libreoffice
- In terminal type:
sudo apt-get autoremove libreoffice-*

this command will remove libreoffice

Second: Install Openoffice:
- In terminal type:
sudo add-apt-repository ppa:upubuntu-com/office

then type:
sudo apt-get update

finally type:
sudo apt-get install openoffice

enjoy it

---

### Post by TenPlus1 on 2012-10-14
LibreOffice is essentially OpenOffice with newer features and an open-source license...

How is OpenOffice better ?

---

### Post by aabed91 on 2012-10-14
when i open documents file or power point files from windows on libreoffice
the style and order of the file changed

but with openoffice it is the same

in other side

in libreoffice i can't write from right to left to write arabic
but in openoffice this is exist.

this is my opinion and your opinion may different :)

---

### Post by Rex Bouwense on 2012-10-14
Libre Office is a fork from Open Office.  They are both open source.  There are probably a few differences I'm sure.

And the OP has listed one very important difference for him.

---

### Post by aabed91 on 2012-10-14
> **Rex Bouwense said:**
> Libre Office is a fork from Open Office.  They are both open source.  There are probably a few differences I'm sure.

Open Office better than Libre Office in my opinion
Because i need to write arabic (Right to left)
and i open a microsoft office files

---

### Post by geoaraujo on 2012-10-14
> **aabed91 said:**
> Open Office better than Libre Office in my opinion
Because i need to write arabic (Right to left)
and i open a microsoft office files
But you can do that with LibreOffice as well...

---

### Post by aabed91 on 2012-10-14
> **geoaraujo said:**
> But you can do that with LibreOffice as well...

i can't find the way to write text from right to lift in Libre Office
it's write arabic but from left to right

in open Office i found this step easily.

---

### Post by mardybear on 2012-10-14
> **aabed91 said:**
> [SIZE="4"][COLOR="Blue"]enjoy it[/COLOR][/SIZE]
Thanks for the post. I'm probably due for an Ubuntu upgrade soon but did not want to give up OpenOffice, as i've been using it for years and it works just peachy for all my documents and spreadsheets.

mardybear

---

### Post by brynhildur on 2012-10-31
I agree with aabed91. Like most of the open source community I switched over to Libreoffice in 2011 and have never been completely happy with it. 

Libreoffice has never been able to synchronize completely with Microsoft Office documents. Documents created in Microsoft are subtly changed in Libreoffice and vice versa.

However, the reason I finally gave up this autumn and decide to give OpenOffice another go was the atrocious way Libreoffice would render documents which were edited using "track changes". I would lose tracked changes in Libreoffice and users of other office systems would have problems with my tracked changes as well. 

And what the hey(!) was that issue with highlighting. As soon as I highlighted a word or a line, it wouldd become permanent and people opening my documents with specific paragraphs highlighted would have to retype them.

Anyways, I tried out OpenOffice again last month and have now removed Libreoffice from all my computers and installed OpenOffice. It works perfectly with Microsoft and vice versa, and for me, that is a dealbreaker.

---

### Post by chideock on 2012-11-01
I did the commands at the top of the post all worked except the last command "sudo apt-get install openoffice" which has the response "unable to locate the package openoffice". I am using Ubuntu 12.10.
 
Any ideas?
 
Thanks
Tom
 
edit add - I see now on the update the system failed to fetch [http://ppa.launchpad.net](http://ppa.launchpad.net)  etc sources and packages error code 404. How does one fix this?
 
Thanks again

---

### Post by sgage on 2012-11-01
I too prefer OpenOffice to LibreOffice. Hard to put my finger on why, but it seems to work better when dual-booting and using files on MS Word as well as OO, vs. LO. Someone else mentioned problems with styles being tweaked - I have noticed this as well.

There are some differences in look'n'feel as well, and though subtle, I prefer OO. The first thing I do on a fresh install is replace LO with OO.

Hurrah for Free Software!

---

### Post by sgage on 2012-11-01
> **doctorcobrado said:**
> libreoffice is good for me... i think i will not replace it if i were you

But you are not me :KS  To each, their own.

---

### Post by Melvyn Gattinoni on 2012-11-13
I'm switching to Open Office too. LibreOffice doesn't only change format in Word documents but also is freezing frequently, menus sometimes don't work and other problems.

---

### Post by samsom63 on 2012-11-13
> **brynhildur said:**
> I agree with aabed91. Like most of the open source community I switched over to Libreoffice in 2011 and have never been completely happy with it. 

Libreoffice has never been able to synchronize completely with Microsoft Office documents. Documents created in Microsoft are subtly changed in Libreoffice and vice versa.

However, the reason I finally gave up this autumn and decide to give OpenOffice another go was the atrocious way Libreoffice would render documents which were edited using "track changes". I would lose tracked changes in Libreoffice and users of other office systems would have problems with my tracked changes as well. 

And what the hey(!) was that issue with highlighting. As soon as I highlighted a word or a line, it wouldd become permanent and people opening my documents with specific paragraphs highlighted would have to retype them.

Anyways, I tried out OpenOffice again last month and have now removed Libreoffice from all my computers and installed OpenOffice. It works perfectly with Microsoft and vice versa, and for me, that is a dealbreaker.

Interesting, I have problems of compatibility between LibreImpress and MS Power Point so I'll give OpenOffice a try.

---

### Post by kiasta on 2012-11-13
> **chideock said:**
> I did the commands at the top of the post all worked except the last command "sudo apt-get install openoffice" which has the response "unable to locate the package openoffice". I am using Ubuntu 12.10.
 
Any ideas?
 
Thanks
Tom
 
edit add - I see now on the update the system failed to fetch [http://ppa.launchpad.net](http://ppa.launchpad.net)  etc sources and packages error code 404. How does one fix this?
 
Thanks again

It might have just been down at the time you were trying to update. Just do another:

```
sudo apt-get update
```

If it is still not working than you might need to just download the .deb from the openoffice.org website. It works fine for me, so I'm not entirely sure why you would not be able to update the repository. Obviously it is not your lack of network connection.

---

### Post by Hagar Delest on 2012-11-15
The best way to install AOO/LibO IMHO is to use indeed the .debs downloaded directly from the official web sites. Note that this way you can install and run both applications in parallel. But my preference goes to AOO of course.

See: [[Ubuntu] Installing OOo on Debian and Co.](http://forum.openoffice.org/en/forum/viewtopic.php?f=74&t=68)

---

### Post by RichardVeevers on 2013-02-26
Srsly, thanks:)
Installed first time for me and as a Linux newbie I'd just struggled to install it from their website.
Regards
Richard

---

### Post by GARoss on 2013-02-27
I agree, Open Office works better for me, too. Libre Office had a glitch or two that were never fixed.

---

### Post by dubious5 on 2013-03-25
I have spreadsheets which work on Open Office which can't be read properly by Libre Office because of the way it handles empty cells. Thanks for your post you have saved me a lot of time!

---

### Post by rrich1974 on 2013-05-02
i think it is a wrong idea that canonical pushes libreoffice as a default office suite in ubuntu. due to my experience, it is not quite easy to completly remove it from the system. especially when i see that a lot of people say thet apache openoffice is better. "me, myself and I" are using apache openoffice on windows and linux and i can say that, when it comes to the compatibility with micro$oft office, it is much better. in fact, i think that libreoffice team should dump the project and join the forces to the apache openoffice to make a better product. 
i will file a bug report because it seems unfair to me that libreoffice is default in ubuntu.

---

### Post by zemega on 2013-05-02
LibreOffice developers work in OpenOffice before, that is before the problem with Oracle and such, they left OpenOffice project and create LibreOffice. OpenOffice has been restarted, and version 4.0 is due somewhen this year, which supposed to better than the curren 3.4. Eithey way, now I have eyes on the WPS Office, albeit its still in beta.

---

