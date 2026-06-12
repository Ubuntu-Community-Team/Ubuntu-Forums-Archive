---
title: "mime types from webdavs servers"
date: 2011-09-17
forum: General Help
---

### Post by zwinsch on 2011-09-17
hallo @all,
this is my first post, after days of serching for a solution, without any results.

I have several webdavs network drives, that I can mount in NAUTILUS via bookmarks.
Some  of them work fine, some are comming upwith only the mimetype  "application/octetstream", (which is translated into  "application/octetstream typ") - for any file-extension. Note: there is  no slash in octetstream! in the mime database there is only the type  "application/octet-stream" registered.
So I added an alias  <alias  type="application/octetstream"/> to the entry in  /usr/share/mime/packages/freedektop.org.xml  and did udate the mime  database.
This changed the situation so far, that now the files type  is translated from "application/octetstream" to  "application/octet-stream" and the friendly name "unknown" is shown.
Not realy the solution, because I can not doubleclick to open with the default appl.
If  I would choose to open the "unknown" filetype always with e.g. gedit,  all files from this server, regardles of .jpg, .txt and so on  would be  opened in future with the same appl. 

Is there any way, to  convince Ubuntu/Nautilus to use for this server connections only the  file extension istead of the mime type comming from the server, to apply  only the mimetyps given in globs?

I am using 10.04 (standard,  not netbook), on an intel netbook. The problem is independend from  wether I use my EN or GE language settings.

I have tried the following Webdavs Servers:

davs://webdav.hidrive.strato.com/   --> works fine
davs://webdav.mc.gmx.net/            --> mime type problem
davs://sd2dav.1und1.de/                --> mime type problem

-- edit Sep 18 --
Furthermore: with any application: On choosing "save as", as soon as I navigate to any location that has this mime typ problem, the dialog and the application crashes. Seems to be caused by a bug?
Via "open with other application" I can open and edit any file from such a location. I also may save it back via menu "File/Save" but  if I choose "File/save as" the application crashes instantanously.

-- end edit --

I also have several FTP servers that I mount in the same way, none of these has shown the problem with the mime types.

In  WinXP I do not have this problem using "Netrive", neither the next yet  unsolved problem, wich could possibley be a separate thread:

There is also an issue regarding different character encodings from different servers. 
Can  anybody tell, which (of the at least 4 - this is very confusing to me)  method NAUTILUS uses, to mount external FTP, SFTP and davs Servers that  are listened in bookmarks ? So I could write my own bash scripts to  mount them manualy and have them afterwards in places, able to unmount  them manualy with one click and without the need of sudo?
Doing so  could (maybe) solve two problems: i) possibly the  encoding to be used  on a certain server could be defined in the script (you can't define it  for servers listed in bookmarks), and ii) I am running out of space in  bookmarks, it would be niche to have only a parent folder in bookmarks  e.g. "WebDrives" wherein you can find all possible web based resources  to mount with a click.

so, now I am eager to see if this can be easily solved by help of the community,
cherrs
Karsten (newbee)

---

