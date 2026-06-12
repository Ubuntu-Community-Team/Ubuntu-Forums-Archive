---
title: "changing an icon in Nautilus and Firefox"
date: 2012-02-07
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-02-07
I'm trying to change a particularly obnoxious low visibility icon that is used in both nautilus and firefox 11. Attached is a tar of it from a screenshot.

I used Ubuntu default "Search for Files" to find every file in the filesystem that had either "left", "arrow", "back", or "previous" in the name and was an image. Then I looked at each of them and renamed the ones that looked like the one I don't like to "[original filename].[original extension]-backup". So, for instance, I renamed "go-previous.png" to "go-previous.png-backup". Then I put in a file of the same type (png or svg or whatever the original was) and same pixel dimensions and same name as the original. So, in the example given, I converted my_image.bmp to a png of the same pixel size as the file I was replacing (48 x 48 for example), copied it to the same directory and renamed it with the name of the original file. I don't see how I could have missed any files unless there is something about "Search for Files" I've misunderstood or Ubuntu would keep files somewhere outside the file system. BTW, I installed this installation of 10.10, Maverick on a single partition, so unless it used one of my data partitions I don't see where it could have put something outside what "Search for Files" and Nautilus both call "File System".

But the icon in Firefox and Nautilus is unchanged. I've rebooted, even cold booted, and it is still unchanged. So when I started this post I tried to attach one of the filename.ext-backup files to the post and I couldn't find one. When I browse those directories (mostly usr/share/icons/gnome/NxN/actions/) the files I renamed *-backup are now copies of the file I made to replace the icon I hate. Which is just plain weird. I AM sober.  This is why I'm attaching an image made by cropping a screenshot rather  than a copy of the icon image itself. Those images seem to have  disappeared from the directories they were in. But not from Nautilus or Firefox.


I am distinguishing image files from shortcuts to image files. I did not at first but I've gone through everything again and made sure the shortcuts have their original names and only the image files they point to have been renamed and replaced with my own creation renamed to the name of the original file.

The only thing I can imagine to account for this is that the images used by firefox and nautilus are NOT named anything containing "left" or "arrow" or "previous" or "back". In which case the only way I can think of searching for the right ones is to use some sort of tool that searches for images visually similar to a known image. Either that or look at every single image in the file system.

I'm stumped. I'd appreciate any suggestions.

---

### Post by Dreamer Fithp Apprentice on 2012-02-07
I forgot the attachment. Here it is.

---

### Post by Dreamer Fithp Apprentice on 2012-04-07
I never did figure out the why of the weirdness described above (and I'd still like to), but for the benefit of anyone who comes to this thread because they were using google or something similar to look for a solution to a similar problem I'll tell you what I have done that works almost as well and what I would do next (and still may) if I wanted to pursue the question as posed.

For the Nautilus or Caja work-around persistent tinkering with the theme customization tools finally got me something I could use. None of the themes I looked at were satisfactory. Those that had decent contrast and visibility in one ap would make text in text entry fields disappear in another and so on, but by repeatedly starting with different themes, by NOT limiting myself to starting with the themes that looked the most promising to begin with, and fiddling with the various customizable components I eventually came up with the one shown in the screenshot which for my eyes on my monitor with my graphics cards works better than anything I've tried. You'll notice the icon in question is still there but at least now I've got it stark white on jet black instead of medium gray on ever-so-slightly-lighter-shade-of-medium-gray. For anyone who is frustrated having to choose between themes with icons they can barely see or themes where they can't see what they are typing into text entry fields or some similar unacceptable tradeoff the point is not that this particular custom theme is your solution because your vision, your graphics card, and your monitor will be different but simply - don't give up, just keep tinkering. I must have tried a hundred modified themes before I found something acceptable for ME. Starting with ones that looked ALMOST right I often ran into dead ends. Some components affect how other components can be customized.  But I kept starting over with different themes. I don't even remember what route I took to get to this one but I know it didn't look at all like the finished product.  

For Firefox, it was much easier to get rid of that obnoxious gray-on-gray icon altogether. There are a LOT more firefox themes than there are Ubuntu themes. Several that are generally strong on legibility can be found at:
[http://www.accessfirefox.org/Firefox_Accessibility_Themes.php](http://www.accessfirefox.org/Firefox_Accessibility_Themes.php)
The one that works best for me though is LCARStrek as modified by the Theme Font & Size Changer extension.  The back button you see in the attached screenshot though is from the extension Big Buttons which I'm still tinkering with although the one that comes with LCARStrek is pretty nice anyway.

OK, those 2 work-arounds are why I'm no longer as motivated to spend time pursuing the answer to the original question as posed but if there is anyone who is interested in that or some similar question and wants to give it some time there are some how-to-make-a-theme tutorial pages at the gnome website that would probably eventually yield the answer and before long there will probably be similar pages at the Mate website .

---

