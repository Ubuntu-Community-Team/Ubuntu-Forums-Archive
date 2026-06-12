---
title: "Mediawiki upload problem"
date: 2009-12-22
forum: General Help
---

### Post by Johannekie on 2009-12-22
Hi,
 
I'm trying to upload .docx files to my wiki. I increased the maximum size for uploads to 20 MB, enable uploads, added the file extension, even checked the mime.type file to see if it is allowed. It was not in the msword applications list so I added it. But I stil get the error:
 
*The file is corrupt or has an incorrect extension. Please check the file and upload again. *
 
And I can upload .txt  and .jpg files but I can't view them.
 
What am I still missing?
 
Any help will be greatly appreciated.
 
Thanks.

---

### Post by Johannekie on 2009-12-22
To get the docx files to work I did the following:
 
$wgEnableUploads       = true;
$wgFileExtensions[] = 'pdf';
$wgFileExtensions[] = 'doc';
$wgFileExtensions[] = 'docx';
$wgFileExtensions[] = 'txt';
$wgUploadPath = "/uploads";
$wgUploadDirectory = "/uploads";
$wgUseImageMagick = true;
$wgImageMagickConvertCommand = "/usr/bin/convert";
[B]$wgVerifyMimeType = false;
[/B]
So now uploads work. But I still cant view the uploaded files. It says:
 
**Warning**: This file may contain malicious code, by executing it your system may be compromised.
 
:confused:
 
And if I click on the link to the file, the following is shown:
 
HTTP 404 not found blah blah blah.
 
Am I doing something wrong with the upload directories or something?

---

### Post by Johannekie on 2009-12-22
I fixed this by commenting out the following:
 
$wgEnableUploads       = true;
$wgFileExtensions[] = 'pdf';
$wgFileExtensions[] = 'doc';
$wgFileExtensions[] = 'docx';
$wgFileExtensions[] = 'txt';
[B]#$wgUploadPath = "/uploads";
#$wgUploadDirectory = "/uploads";
[/B]$wgUseImageMagick = true;
$wgImageMagickConvertCommand = "/usr/bin/convert";
$wgVerifyMimeType = false;

This worked perfectly for uploads.
 
Now if I try to download the file which I uploaded, it "sees" it as a .zip file. From what I can understand this has something to do with MIME Types, but I have no idea how to fix it.
 
Any ideas?

---

