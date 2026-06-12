---
title: "How to edit realtime a Web Site via an FTP connection with Kompozer?"
date: 2011-11-07
forum: General Help
---

### Post by apollothethird on 2011-11-07
Does anyone know how to use Kompozer to edit current web sites using ftp (similar to the way Dream Weaver works)?

At present, following everything I can find, I can setup a new site in the site manager.  It prompts for a local directory.  I can work on that local directory, create a page and do a lot of things.  I can also eventually publish the page I edit.

However, I'm trying to configure the site manager so that the page I'm working with is the ftp page.  I can't figure out how to get it setup so that I can use that side frame feature to browse a page on an ftp site and edit those pages already there.

I have a lot of hierarchies of directories and files that would be cumbersome to try to get everything on my local hard drive just to make a simple change.  I'm sure I'm missing something simple.  If someone is able to do this can you tell me how you're doing it?

Thanks in advance for any suggestions or comments.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by drdos2006 on 2011-11-07
Have a look at this thread.
[http://ubuntuforums.org/showthread.php?p=11435150#post11435150](http://ubuntuforums.org/showthread.php?p=11435150#post11435150)

regards

---

### Post by apollothethird on 2011-11-08
> **drdos2006 said:**
> Have a look at this thread.
[http://ubuntuforums.org/showthread.php?p=11435150#post11435150](http://ubuntuforums.org/showthread.php?p=11435150#post11435150)

regards

Thanks for the links.  The information provided in those links are duplicates of everything I've already done that doesn't work.  Some of them links to sites that I had already visited.  It appears to be very straight forward and seamless, but it doesn't work.

As I mentioned, I can click on the publish button and publish something I'm working on locally, but there doesn't appear to be a way to work on a remote file and save the remove file you're working on.  You can only work on a file that is either not saved or saved on the local machine then publish it.  Even the publich option only works one time.  If I make another change the publish button isn't selectable.  The only think I can do is save it locally, close Kompozer then start Kompozer again and publish it.

If anyone has the feature working can you chime in?

I have a test site where the page is: [http://fsd.apollo3.com/~ljames/test]("http://fsd.apollo3.com/%7Eljames/test")

I can ftp into the site with:

```

ftp fsd.apollo3.com
ljames
password
cd public_html/test
get index.html
(work on the file locally)
put index.html

```This is what I have in the Site Manager of Kompozer:

```

->General Settings<-
Site Name:                           Kompozer Test
Site Folder                           /home/ljames/kompozertest
HTTP address of page:     http://fsd.apollo3.com/test
Prefix:                                    public_html/test

->FTP Settings<-
Publishing address:           ftp://fsd.apollo3.com
User name:                          ljames
Password:                            XXXXXXXXXX

```I have tried lots of other combinations.  Can someone look at this and tell me where I might be going wrong or something I can change and test and let you know the results.

I'm using the version which is the latest version number from the Kompozer's Web Site which is the one that was installed via Synaptic.  It's version 0.8b3 (20081229) (c) 1998-2010

Thanks in advance for any suggestions or comments.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

