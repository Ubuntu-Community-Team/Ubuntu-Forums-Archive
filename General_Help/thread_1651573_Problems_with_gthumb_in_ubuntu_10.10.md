---
title: "Problems with gthumb in ubuntu 10.10"
date: 2010-12-23
forum: General Help
---

### Post by UeB on 2010-12-23
Hallo,

I have Problems with current version of gthumb 2.11.3 which is the default version in ubuntu 10.10.

My 2 main problems:

the browser shows not only Images but also video and other files but I don't want to see them!

There is a flag in one can edit in the gconf editor that prevents non image files to be shown: /apps/gthumb/browser/show_only_images but the new version of gthumb seems to ignore this flag. (this flag worked fine with old version of gthumb)

the browser and the "next" button in the show pictures in a strange order I just want to see my image files sorted by there file name as it was before and I cannot find the option to make this happen.
I have no idea what gthumb is using at the moment to sort images in the browser but whatever order it is, it is useless for me

what I already tried: upgrade gthumb to version 2.12.1
but this did not change any of the 2 problems I described


thanks in advance 
and kind regards

---

### Post by UeB on 2010-12-23
Can somebody at least tell me if they have the some problems OR if there are not experiencing this problems so I can know if this a an issue of the there specific version of gthumb OR if something is wrong with my configuration or version of gthumb.

kind regards

---

### Post by mjc1 on 2010-12-23
Use 2.12.x, not 2.11.x.
[https://launchpad.net/~webupd8team/+archive/gthumb](https://launchpad.net/~webupd8team/+archive/gthumb)

To stop showing video files, go to View>Filter and set the "General Filter" to "Images".

To change the sorting order, use View>Sort By.

- Mike

---

### Post by Ubunthree on 2010-12-23
GThumb works that way for me too now.

My own issue with the new gThumb is that you can't run multiple instances any more, say if you want to compare two versions of an image side-by-side on the screen, and I can't find a GConf option for that either. I have switched to Mirage for the time being. I never used gThumb as an album manager, just as a general image viewer, and I do all my photo editing with GIMP anyway, so for me Mirage is a usable substitute. I'm OK with gThumb including videos etc., and it's probably improved in other ways for a lot of people, but the older version suited my own needs a little better. GThumb still does the importing from my camera's SD card, though, which works OK.

Sorting by name is annoyingly inconsistent among various applications. The image viewers and file managers that I have order files differently. Try putting a few images into a test folder and naming them with various mixes of letters and numbers, and see whether your gThumb is at least behaving by its own rules. On my system things seem to work like this...

Mirage sorts purely alphabetically, like this:

04test.jpg
28th.jpg
3speed.jpg
747.jpg
abbymouse_1920.jpg
abbymouse_2.jpg
alcazar_1920.jpg
a_mill.jpg
a-mill.jpg


GThumb, Eye of GNOME, Nautilus, and the system open/save dialogs seem to treat number characters as numeric values wherever they appear in the filename, like this:

3speed.jpg
04test.jpg
28th.jpg
747.jpg
abbymouse_2.jpg
abbymouse_1920.jpg
alcazar_1920.jpg
a_mill.jpg
a-mill.jpg

The Thunar file manager sorts numerically as well, but unlike all of the others, it ranks underscores and hyphens higher than letters, like this:

3speed.jpg
04test.jpg
28th.jpg
747.jpg
a_mill.jpg
a-mill.jpg
abbymouse_2.jpg
abbymouse_1920.jpg
alcazar_1920.jpg

It's possible to name files so that alphabetical and numeric sorting come out the same (using 005 and 012 instead of 5 and 12 for example), but it's not always easy.

---

### Post by Ubunthree on 2010-12-23
> To stop showing video files, go to View>Filter and set the "General Filter" to "Images".

Thanks; I had overlooked that myself.

After a bit of fiddling, what I gather is that you can use the filters to allow more than one media type also, but you have to create your own filters, and the process is not very intuitive. What you have to do to make the viewer display, for example, video and text files only, with no images, is:

View > Filter

"New" button

Give your filter a descriptive name like "Video/Text"

Check the "Match" box, and select "any of the following rules"

Set the rules label to "Video"

Click the + over to the right to add another rule; set that to "Text Files"

"Save" button when you're done

Put gThumb into Browser mode. Make sure the View menu has "Filterbar" enabled. The "Show" button on the Filterbar at the bottom of the window lets you pick any enabled filter that you have. If you don't see one that you think you have, select "Personalize..." to bring up the Filters dialog again, and make sure the filter you want actually exists and is enabled in the "Other filters" box. With your filter selected, the viewer should now display only those file types allowed by the filter.

A bit cumbersome maybe, but it works at least, assuming I'm doing it right.

---

### Post by UeB on 2010-12-23
> **mjc1 said:**
> Use 2.12.x, not 2.11.x.
[https://launchpad.net/~webupd8team/+archive/gthumb](https://launchpad.net/~webupd8team/+archive/gthumb)

To stop showing video files, go to View>Filter and set the "General Filter" to "Images".

To change the sorting order, use View>Sort By.

- Mike

thanks this suggestions helped a lot!

---

### Post by mjc1 on 2010-12-24
> **Ubunthree said:**
> My own issue with the new gThumb is that you can't run multiple instances any more, say if you want to compare two versions of an image side-by-side on the screen, and I can't find a GConf option for that either.

Does File>New Window work?

> Sorting by name is annoyingly inconsistent among various applications.

Sorting is actually a complicated problem, especially if you take into account unicode and locale-specific language sorting rules. However, gnome applications should all use the g_utf8_collate and g_utf8_collate_key_for_filename functions, described here: [http://library.gnome.org/devel/glib/stable/glib-Unicode-Manipulation.html#g-utf8-collate](http://library.gnome.org/devel/glib/stable/glib-Unicode-Manipulation.html#g-utf8-collate)

That is why nautilus, gthumb, and eog all follow the same rules. Since mirage is a gtk app, it should too. You might want to file a bug report with mirage if it uses a different sorting scheme. I imagine they'd like to follow the nautilus conventions as well.

- Mike

---

