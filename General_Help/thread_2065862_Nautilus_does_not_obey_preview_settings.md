---
title: "Nautilus does not obey preview settings"
date: 2012-10-03
forum: General Help
---

### Post by MrsUser on 2012-10-03
Hello dear Ubuntu users,

I have a problem with Nautilus and would like to know if others have the same issue. As I have many big video files on my computer and also some big sized photos, I wanted to switch off thumbnailing for big files. However, I want to keep thumbnailing for small sized files.

Now, when I set in Nautilus' preferences:

[[IMG]http://i.imgur.com/9tT7Us.png[/IMG]]("http://imgur.com/9tT7U")

Preview > 'Other Previewable Files'
Show thumbnails: Local Files Only
Only for files smaller than: 5 MB

then [COLOR=DarkRed]Nautilus should show thumbnails only for files smaller than 5 MB[/COLOR]. However, Nautilus obeys this preference only for pictures, not for any other files.[COLOR=DarkRed] But Nautilus still generates thumbnails for video and pdf[/COLOR] [COLOR=DarkRed]files[/COLOR] (and perhaps other file types), no matter what file size they have. This is, of course, very annoying when you open a folder with dozens of big sized video or pdf files.

This happens on a fresh install of Ubuntu 12.04.1 64-bit. And I wonder how I can fix this.

---

### Post by ishneww on 2013-04-01
I faced the same problem. After some research I found only one solution. I installed dconf-tools and in dconf editor I found an option to disable external thumbnailer.
After disabling the external thumbnailers, nautilus was only showing preview of images. It solved my problem. In dconf editor you will find this option in this way - org > gnome > desktop > thumbnailers > disable-all. I am also attaching a screenshot. Hope this will help you. :p

---

