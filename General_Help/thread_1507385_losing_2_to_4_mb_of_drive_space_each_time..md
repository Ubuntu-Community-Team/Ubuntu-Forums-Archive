---
title: "losing 2 to 4 mb of drive space each time."
date: 2010-06-11
forum: General Help
---

### Post by skubo on 2010-06-11
dell mini 9
sometimes when downloading a file, only a save window opens and it gets sent to /tmp .
instead of the open save window that lets me choose the location.

i has to move it to a flash drive then del. it from trash to get that memory space back.
what other locations can files hide in or get sent to.

youtube type videos are running out drive space.
would gsn.com ads and games have backup files anywhere?

i has the cache set to 0mb.
where does gedit put a backup when it opens a file.


123.8mb
131.6mb 
137.4mb
after uninstalling old kernel packages

i has mail set to stay on server and only download when i tells it.

i installed anjunta and saved some mail, then it droped to.
117.6mb 
without saving anything it droped to
115.2mb

at 7.5mb in droped to 
3.7mb
i deleted cookies, changed history to 20days then instead of increasing it droped to
20kb

switched to classic desktop got some errors, logged out back in to get the desktop to load all the way , switched back to dell desktop. and free space was back up to
3.9mb

went on gsn , mail web site free space now
3.4mb

i wanted to try moving the mailfolder i made to a flash drive but i think something
else is would still take free space at 2 to 4mb at a time.
does sorting mail into folders take up more space than one.


is thier a way to know what files belong in ubuntu and thier proper size.
disk usage analyzer
home scan    100%  581.1mb   79 items
 .evolution  37.6%  218.4mb 11 items
 -mail 90.1%  196.7mb   6 items
  --local    61.1%  120.1mb  318 items
  --pop      38.8%  76.3mb
 -cache     9.8%   21.5mb  2 items
100% http all 2 digit hex file names 64 items

?? whats the difference between local and pop

thiers only 2 items listed under local with 6 and 2 items

 .thumbnails   6.0%  34.8mb

 .adobe  2.6mb  4 items
  -flash_player   93.0%  2.4mb
   -assetcache     99.8%  2.4mb
    --zlz24bss   99.8%  2.4mb  13 items
        it does not show the 13 items
  

.mozilla   46.4%   269.4mb  4 items
 -firefox   97.9%   263.9mb  2 items
 --3cbef544.default  100%  263.8mb   35 items
   cache 1.8%   4.8mb   46 items

/home/orac/.evolution/mail/pop/mail@server/cache   76.2mb  64 items
the green one on the map.


scan filesystem
/   100%   3.2gb    23 items
 usr   64.7%  2.1gb
 home   17.7%   581.1mb
 var   7.2%    237.6mb
 media   3.8%   124.5mb
 opt     3.6%    117.8mb

 boot .3%   9.2mb
 usr/share   1.1gb

opt/adobe/reader8/reader/intellinux   101.8mb

---

### Post by skubo on 2010-06-17
how much free space does firefox-optimize.sh need to work.

orac@orac:~$ sqlite3 $HOME/.mozilla/firefox/3cbef544.default/places.sglite "vacuum"
orac@orac:~$ sqlite3 $home/orac/.mozilla/firefox/3cbef544.default/places.sqlite "vacuum"
Unable to open database "/orac/.mozilla/firefox/3cbef544.default/places.sqlite": unable to open database file
orac@orac:~$ sqlite3 $home/orac/.mozilla/firefox/3cbef544.default/places.sqlite "vacuum"
Unable to open database "/orac/.mozilla/firefox/3cbef544.default/places.sqlite": unable to open database file
orac@orac:~$ sqlite3 /home/orac/.mozilla/firefox/3cbef544.default/places.sqlite "vacuum"
SQL error: disk I/O error
orac@orac:~$ chmod +x /home/orac/firefox-optimize.sh
orac@orac:~$ firefox-optimize.sh
bash: firefox-optimize.sh: command not found
orac@orac:~$ run firefox-optimize.sh
bash: run: command not found
orac@orac:~$ /home/orac/firefox-optimize.sh
firefox: no process killed
Please wait while the databases are optimized...
SQL error: disk I/O error
SQL error: disk I/O error
Firefox databases optimized with success!
orac@orac:~$ /home/orac/firefox-optimize.sh
firefox: no process killed
Please wait while the databases are optimized...
SQL error: disk I/O error
SQL error: disk I/O error
Firefox databases optimized with success!
orac@orac:~$ sqlite3 /home/orac/.mozilla/firefox/3cbef544.default/places.sqlite "vacuum"
SQL error: disk I/O error
orac@orac:~$ 


it looks like 'clear privet data' not working and when i tries
menu/places/recent documents/clear recent documents.
free space drops to 0.

3cbef544.default/places.sqlite = 195.1mb
urlclassifier3.sqlite = 59.1mb
/home/orac/.recently-used.xbel =429.3kb

/home/orac/.mozilla/web browser.bak/ web browser/3cbef544..default/cache

/home/orac/.mozilla/web browser.bak/4aceecmq.default
    this one has bookmark backups from 2009 and places.sqlite = 1.1mb

web browser link   has 72 items 266.6mb, link target /home/orac/.mozilla/firefox
not sure what the link is used for is it normal.
can 4aceecmq.default be deleted without crashing.

firefox/3cbef544.default/cache   had 44 items
12 g-zip archives of an unsupported format
_cache_003_ = 2.2mb,  whats in it 
should only the lower numbers be deleted.

when i tried to copy .mozilla to a sd card , had to skip lock files
/lock  link target: 127.0.0.1:+13662
type: link (broken)

when i went to /var/run/sudo/orac  2items,it said free space was 500.3mb.

---

