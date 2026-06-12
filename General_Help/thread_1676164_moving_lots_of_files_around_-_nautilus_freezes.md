---
title: "moving lots of files around - nautilus freezes"
date: 2011-01-26
forum: General Help
---

### Post by Awareness on 2011-01-26
does anybody know a nice way to move lot of files around?

I use nautilus and its awful. The only good thing are the tabs and the bookmarks

on the cons:
* it freezes now and then when moving lots of files.
* Slow to navigate while large amounts of data are moving or displaying.
* Slow presenting of files where there are a lot of them (it should only render whatever is in screen and maybe render a properly sized navigation bar. Anything else shouldnt freeze the client. Render at its once pace if at all. I dont move the scroll bar it shouldnt freeze:(
* It doesnt queue (meaning it moves everything at the same time instead of queueing stuff, what makes moving stuff take longer) . 

Does anybody know anything that allows more than 2 tabs and has a reliable copy?

---

### Post by quadproc on 2011-01-26
> **Awareness said:**
> does anybody know a nice way to move lot of files around?

You will probably find that rsync is a good tool for this task.  Of course, it is a command line tool so you won't get a fancy screen, you'll just get results.

quadproc

---

### Post by LewRockwellFAN on 2011-01-26
You could use Thunar or Roxy instead. They are much quicker and use less memory. I've had similar problems with Nautilus and it was suggested by someone here to turn off thumbnails. That was maybe a day or two ago and so far Nautilus hasn't bogged down on me. A little early to say if it worked cause the problem was always intermittent and I haven't done a lot of file moving since.

---

### Post by Awareness on 2011-01-26
I did know about rsync. It just doesnt suit the porpurse im looking for. :(

I cant fast copy and paste between tabs. And easy and FAST selecting like i can with a gui tool. Ill try out some rsync gui tho.

---

### Post by Awareness on 2011-01-27
> **LewRockwellFAN said:**
> You could use Thunar or Roxy instead. They are much quicker and use less memory. I've had similar problems with Nautilus and it was suggested by someone here to turn off thumbnails. That was maybe a day or two ago and so far Nautilus hasn't bogged down on me. A little early to say if it worked cause the problem was always intermittent and I haven't done a lot of file moving since.

I will try thunar and roxy. One of my big issues is to be able to queue movements, instead of doing all together. With more than 2 tabs would be explendid

---

### Post by LewRockwellFAN on 2011-02-07
I maybe should have mentioned Thunar doesn't have tabs. To me that's its biggest drawback. However you can right click on anything you would have opened in a new tab and open a new WINDOW instead. Once you get used to it it is almost as convenient as tabs. Not quite. Another irritation with Thunar relevant to file handling is its misnamed "delete" right-click menu item. If you sometimes delete massive files or file trees it takes an inordinate amount of time approximately equal to [(1/e x the age of the earth) + (mean time for women to return borrowed books)]. You can easily add a delete-for-real function as a context menu item, complete with (or without) confirmation but you'll have to remember "delete" doesn't mean delete 'cause you can't rename the "delete" item that really means "move this to our special hidden trash bin on another partition, 'cause we think you're a retard that can't be trusted to delete files and we know you've got half an hour to spare while we copy these".

On Nautilus being less of a memory hog with thumbnails disabled, it seems to be true. I'm not sure yet if it ELIMINATES the memory leak or, as I suspect, just drastically slows it down, so that it takes a lot longer before it is tying up enough memory to be a problem.

---

