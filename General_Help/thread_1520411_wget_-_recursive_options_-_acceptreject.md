---
title: "wget - recursive options - accept/reject"
date: 2010-06-29
forum: General Help
---

### Post by Zzzzzzz1 on 2010-06-29
Hello!

Ubuntu newbie looking for some quick help on wget.

I'm trying to use wget to do something that I'm guessing is fairly simple, but haven't been able to get it to work.  Here's the deal:

1) I would like to download all files that include a particular sequence of characters in the file name from a website.  The site is http.

2) The website has a heirarchy of links that includes one link for each year, under which there are certain zip files that I want to download, and some that I don't want.  

3) The names of the files that I want are the same in any given year.  For example - the direct links for each individual files that I want to download would be something similar to the following:

[http://website/2008/First_file_I_want.zip](http://website/2008/First_file_I_want.zip)
[http://website/2008/Second_file_I_want.zip](http://website/2008/Second_file_I_want.zip)

[http://website/2009/First_file_I_want.zip](http://website/2009/First_file_I_want.zip)
[http://website/2009/Second_file_I_want.zip](http://website/2009/Second_file_I_want.zip)

[http://website/2010/First_file_I_want.zip](http://website/2010/First_file_I_want.zip)
[http://website/2010/Second_file_I_want.zip](http://website/2010/Second_file_I_want.zip)

4) There are also several files in each year that I don't want, thus - the following items would need to be excluded from the download:

[http://website/2008/files_I_DON'T_want.zip]("http://website/2008/files_I_DON%27T_want.zip")
[http://website/2009/files_I_DON'T_want.zip]("http://website/2009/files_I_DON%27T_want.zip")
[http://website/2010/files_I_DON'T_want.zip]("http://website/2010/files_I_DON%27T_want.zip")

I've tried the accept/reject command as follows, but nothing gets download:

wget -A '*file_I_want.zip' [http://website/](http://website/)

What am I missing?  I've reviewed the man page for wget and hunted through the forums, and it seems as though this should work.

Many thanks in advance for any help!!!

---

### Post by Zzzzzzz1 on 2010-07-04
If anyone is interested, I found the solution here.  The wget manual isn't very clear on this, but it looks to me as though http:// sites cannot be downloaded with wildcards (i.e.  "-A '*file_I_want.zip'" won't work for non-ftp sites).  Thus, I used brute force (using OpenOffice calc) to create a list of direct links, each one with an individual wget instance, and downloaded that way.  Pretty inelegant, but it worked.

---

