---
title: "wget : restrict download to specific directory"
date: 2010-07-27
forum: General Help
---

### Post by techbrainless on 2010-07-27
Hi All,

I am trying to download site using wget : 

$sudo wget -r -Nc -mk [http://code.google.com/codejam/](http://code.google.com/codejam/)

but it is downloading the contents of  all directories and subdirectories under the domain : [http://code.google.com/](http://code.google.com/) (ignoring the 'codejam' directory)

so it is downloading from links like : 
[http://code.google.com/codejam/](http://code.google.com/codejam/)
[http://code.google.com/apis/ajax/](http://code.google.com/apis/ajax/)
[http://code.google.com/appengine/](http://code.google.com/appengine/)
....etc


i want to restrict the download so that wget command should download only the things under 'codejam' directory

---

### Post by typal on 2010-07-27
Would 
```
wget [http://code.google.com/codejam/](http://code.google.com/codejam/)*

```
work?
Just an idea.

---

### Post by techbrainless on 2010-07-27
thanks for the reply 
i executed the command 
```
$sudo wget -r -Nc -mk http://code.google.com/codejam/*
```


but got error 

```
Warning: wildcards not supported in HTTP.
--2010-07-27 23:40:47--  http://code.google.com/codejam/*
Resolving code.google.com... 74.125.115.102, 74.125.115.113, 74.125.115.138, ...
Connecting to code.google.com|74.125.115.102|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-07-27 23:40:47 ERROR 404: Not Found.

Converted 0 files in 0 seconds.
```

any other suggestion...

---

### Post by techbrainless on 2010-07-27
Hi All , 

I have added the option 
 ```
--include-directories
```and it works for me , now the command is 
```
$sudo wget -r -Nc -mk   --include-directories=codejam http://code.google.com/codejam/
```
but the problem now is that some of pages ( non .html extention pages ) are not displaying and got error
file not found

example for such pages : [http://code.google.com/codejam/contest/dashboard?c=639102#](http://code.google.com/codejam/contest/dashboard?c=639102#)

by the way  .html extention pages have downloaded properly

---

### Post by typal on 2010-07-27
I think this is the type of command you are looking for:
[http://www.linuxjournal.com/content/downloading-entire-web-site-wget](http://www.linuxjournal.com/content/downloading-entire-web-site-wget)
I'm guessing dropping the windows option would be your way to go, though.

---

### Post by techbrainless on 2010-07-28
thanks for the reply.

[HTML]I think this is the type of command you are looking for:
http://www.linuxjournal.com/content/...-web-site-wget
I'm guessing dropping the windows option would be your way to go, though.     [/HTML]I have checked the above link and execute the following 2 commands separatly
```
wget --recursive --no-clobber --page-requisites --html-extension --convert-links --restrict-file-names=windows --domains code.google.com --no-parent  --include-directories=codejam  http://code.google.com/codejam
``````
wget --recursive --no-clobber --page-requisites --html-extension --convert-links  --domains code.google.com --no-parent  --include-directories=codejam  [http://code.google.com/codejam](http://code.google.com/codejam)
```none of above 2 commands can download the none .html pages 
properly ( page like [http://code.google.com/codejam/contest/dashboard?c=639102#](http://code.google.com/codejam/contest/dashboard?c=639102#))

any suggestion

---

### Post by techbrainless on 2010-07-28
any suggestion

---

### Post by techbrainless on 2010-07-29
any suggestion

---

### Post by felix-leg on 2010-07-29
It downloads all, but it puts wrong SRCs and HREFs in links:
```
<div id="logo-div">
  <a href="**/codejam**">
    <img src="**/codejam/contest/static/logo_image4.gif**" id="logo" alt="Google
         Code Jam">
  </a>
</div>

```If for example you have got all into */home/user/Downloads/code.google.com/codejam* the above links will try to tell your browser to look into */codejam* directory **in the root of your file system** instead of **your home directory**. 

I had resolved it in this way:

First, I have let it download a few pages, then I stop it. I wrote down where are the files (especially *index.html*) 

Second, I run the command again with a new option:
> wget --recursive --no-clobber --page-requisites --restrict-file-names=windows --domains code.google.com --no-parent **--base=file:///{your-written-down-directory}** --convert-links  --include-directories=codejam  [http://code.google.com/codejam](http://code.google.com/codejam)

And all images,css,js works fine :)

---

### Post by techbrainless on 2010-07-31
hi felix-leg , thanks for your reply,

thanks for the reply , but now am not looking for  answer for the question "restrict download to specific directory" , i have already successed in doing that.

my question now is why none .html pages
( page like [http://code.google.com/codejam/conte...oard?c=639102#](http://code.google.com/codejam/conte...oard?c=639102#)) are not downloading properly ? (there is a porblem in downloading dynamic data)

just check my previous replies

---

### Post by dino99 on 2010-07-31
im using an other synaptic pakage: webhttrack

WebHTTrack is an offline browser utility, allowing you to download a World
Wide website from the Internet to a local directory, building recursively
all directories, getting html, images, and other files from the server to
your computer, using a step-by-step web interface.

WebHTTrack arranges the original site's relative link-structure. Simply
open a page of the "mirrored" website in your browser, and you can
browse the site from link to link, as if you were viewing it online.
HTTrack can also update an existing mirrored site, and resume
interrupted downloads. WebHTTrack is fully configurable, and has an
integrated help system.

 Snapshots: [http://www.httrack.com/page/21/](http://www.httrack.com/page/21/)

---

### Post by techbrainless on 2010-07-31
Hi dino99 thanks for the reply , 

I have downloaded the site [http://code.google.com/codejam/](http://code.google.com/codejam/) 
using webhttrack , but still the same the problem exists,

none .html pages
( page like [http://code.google.com/codejam/conte...oard?c=639102#](http://code.google.com/codejam/conte...oard?c=639102#)) are not downloading properly ? (there is a porblem in downloading dynamic data)

---

### Post by techbrainless on 2010-08-01
any suggestion

---

### Post by felix-leg on 2010-08-01
All right I recheck the problem, and I think I have bad news. Pages are downloaded properly, but in this case it is not enough. These specific pages you're asking about a Google service downloads through **AJAX**. It works fine in a browser because the browser have an ability to **execute** JavaScript on pages. So if any site-downloader would like to work with such pages it must also be able to execute JS and, moreover, replace previously gotten content with a new one generated by the script. 

Well, site-copy was much easier before AJAX invention :(. You should look for a program with an explicitly written attestation in its documentation that I was designed to deal with AJAX.

---

