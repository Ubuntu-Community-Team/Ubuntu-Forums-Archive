---
title: "MediaWiki/Uploads/MIME Types/Office 2007"
date: 2010-01-28
forum: General Help
---

### Post by foetoid on 2010-01-28
Hi all,

First post, however I've been trolling these forums for tips and tricks for quite some time now. I'm looking for some help on getting the MIME types setup correctly for Apache/MediaWiki. I think I've modified every config file known to man to no avail. Here's some info on what I've got going on.

I'm trying to get the Office 2007 MIME types configured for MediaWiki 1.14 so that we can upload/download the files. Out of frustration/lack of need I went the less secure route and I modified the LocalSettings.php config file to disable MIME type verification for uploads.

```
$wgVerifyMimeType = false;
```

This works great for the uploads, and I can upload .DOCX, .XLSX, and .PPTX all day long, however when downloading them, they download as a .ZIP file with all the XML info inside of it. No biggie for me personally as I can just rename .ZIP to .DOCX and it works fine, however for the average user it's not going to fly.

So, I figured that MIME types would be the source of my pain and started doing some research.

I have modified the following config files to include the MIME types listed below.

/etc/mime.types
/var/www/.htaccess (created to try and force them)
/var/www/mediawiki-1.14.0/.htaccess (created to try and force them)
/var/www/mediawiki-1.14.0/includes/mime.types

```

application/vnd.ms-word.document.macroEnabled.12 .docm
application/vnd.openxmlformats-officedocument.wordprocessingml.document docx
application/vnd.openxmlformats-officedocument.wordprocessingml.template dotx
application/vnd.ms-powerpoint.template.macroEnabled.12 potm
application/vnd.openxmlformats-officedocument.presentationml.template potx
application/vnd.ms-powerpoint.addin.macroEnabled.12 ppam
application/vnd.ms-powerpoint.slideshow.macroEnabled.12 ppsm
application/vnd.openxmlformats-officedocument.presentationml.slideshow ppsx
application/vnd.ms-powerpoint.presentation.macroEnabled.12 pptm
application/vnd.openxmlformats-officedocument.presentationml.presentation pptx
application/vnd.ms-excel.addin.macroEnabled.12 xlam
application/vnd.ms-excel.sheet.binary.macroEnabled.12 xlsb
application/vnd.ms-excel.sheet.macroEnabled.12 xlsm
application/vnd.openxmlformats-officedocument.spreadsheetml.sheet xlsx
application/vnd.ms-excel.template.macroEnabled.12 xltm
application/vnd.openxmlformats-officedocument.spreadsheetml.template xltx 		

```

It doesn't seem to matter where I put the code, I can't get the MIME types to register with Apache/MediaWiki. Any thoughts or ideas would be super helpful.

Thanks

---

### Post by jasonralston on 2010-03-19
I have a simular problem. I I've added .docx = application/vnd.openxmlformats-

to /etc/mime.types
and to /etc/apache2/mods-available/mime.conf

Doesn't do a thing???????? 

I see you haven't got a response either? 

I'm running Ubuntu Server 9.10

---

