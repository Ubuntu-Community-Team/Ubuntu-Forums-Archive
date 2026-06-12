---
title: "How to stop automatic thumbnail creation and storage?"
date: 2011-01-31
forum: General Help
---

### Post by maspeir on 2011-01-31
I was lurking about my hidden files and noticed the ".thumbnails" directory. I had been browsing the web for about an hour and had opened some image files from my drive.

HOLY CRAP! I had over 2000 thumbnails in that directory! Every time an image is displayed, a thumbnail of it is created? Really?:-s:shock: Seriously, I don't care what the reason behind this "feature" is, how do I stop it? It is simply unnecessary and a waste of disk space.

---

### Post by cchhrriiss121212 on 2011-01-31
> It is simply unnecessary and a waste of disk space.
On the contrary it helps images load faster and will not use more than a set amount of drive space. In any case see this to edit or disable the feature:
[http://http://en.kioskea.net/faq/2725-clearing-the-thumbnail-cache-on-linux]("http://http//en.kioskea.net/faq/2725-clearing-the-thumbnail-cache-on-linux")

---

### Post by derklempner on 2011-01-31
> **maspeir said:**
> Seriously, I don't care what the reason behind this "feature" is, how do I stop it? It is simply unnecessary and a waste of disk space.
Open Nautilus, and go to Edit --> Preferences --> Preview --> Show Thumbnails --> Never.

No offense, but it took me a whole 10 seconds to Google "ubuntu disable .thumbnails" to find this answer.  You should be able to find answers as basic as this by simply Googling the problem.  If you can't find the answer, then we're always here to help.  :D

---

### Post by drewsus on 2011-01-31
I have 8096 thumbnails in there, but it only takes 87MB, so its really not that big of a waste of space... and its necessity is debatable.

---

### Post by maspeir on 2011-01-31
> **derklempner said:**
> Open Nautilus, and go to Edit --> Preferences --> Preview --> Show Thumbnails --> Never.

No offense, but it took me a whole 10 seconds to Google "ubuntu disable .thumbnails" to find this answer.  You should be able to find answers as basic as this by simply Googling the problem.  If you can't find the answer, then we're always here to help.  :D

I did find it in a Google search, but it took more than 10 seconds! :p

However, the instructions you gave do not work. There isn't anything in the Nautilus preferences that refers to thumbnails. I had to do this from the file system. Is Nautilus the GUI in Ubuntu? Maybe I'm getting terms mixed up?


> **drewsus said:**
> I have 8096 thumbnails in there, but it only takes 87MB, so its really not that big of a waste of space... and its necessity is debatable.

My concern is that it is done without asking or alerting the user and image files take up lots of space. This is all done transparent to the user and that is a bad thing. After doing a Google search, I find that not only does Nautilus create thumbnails for all files in a given directory, it recreates them without deleting the old thumbnails. I hate to say it, but the way Windows does this is far more elegant.

Anyway, thanks for the info. Problem is solved.

---

### Post by drewsus on 2011-01-31
nautilus is the GUI for your file browsing. If you open your home directory, you are doing so with Nautilus. 
Press Alt+F2 then enter in "nautilus" and pretty Enter. 
Then, go to Edit --> Preferences --> Preview --> Show Thumbnails --> "And set all options to Never"

---

### Post by drewsus on 2011-01-31
> but the way Windows does this is far more elegant.
Explain. How do they do it more transparently and how is it more elegant? And again, *"image files take up lots of space"* is highly debatable seeing as my 8000+ took a mere 87MB.

---

### Post by cchhrriiss121212 on 2011-01-31
The maximum space it will take up is 512MB, which is not much nowadays. After that the files are deleted. Like I said, you can change that value easily.

---

### Post by maspeir on 2011-01-31
> **drewsus said:**
> Explain. How do they do it more transparently and how is it more elegant? And again, *"image files take up lots of space"* is highly debatable seeing as my 8000+ took a mere 87MB.

87 MB isn't all that much (I have a 1 TB drive) and I am aware of the 512 MB limit.

To clarify my "elegant" comment:

1.) Windows stores the thumbnails in the directory with the files. Yes, they are hidden, but I don't have to dig if I want to remove them.
2.) Windows only creates the thumbnails when the user chooses to view the files as thumbnails.
3.) If I have a directory with, say, five images, only five thumbnails will be created. If I edit one of those images and then right-click and choose "refresh", the five thumbnails (at worst) are updated, but I will still only have five thumbnails.
4.) If the file is not conducive to being displayed as a thumbnail, Windows does not make a thumbnail.
5.) If I delete a file, the associated thumbnail is deleted.

All of these points, as I currently understand it and as I have found via Google, are contrary to how it is done in Ubuntu. I'm not saying that Windows is better at everything, but it does seem to have the upper hand here.

My transparent comment is referring to the fact that it is immediately assumed that the user wants thumbnails and the option is not easily found. I want thumbnails if I choose to and then, only in the directory that I specify. I may have a directory of PDFs and one of images and only want the images to have thumbnails. Moreover, all web browsers store images in their own cache, so making thumbnails from images displayed on a web site is both pointless and counterproductive.

Essentially, the process of thumbnail creation in vs. 10 of Ubuntu, IMO, seems flawed.

---

### Post by cchhrriiss121212 on 2011-01-31
> To clarify my "elegant" comment:
Point 1 is not necessarily more elegant, it is just different. Points 2-5 will only have a negative impact on disk usage, which we agree is a minute value.
> My transparent comment is referring to the fact that it is immediately assumed that the user wants thumbnails and the option is not easily found.
Ubuntu is designed to be user friendly and that means making a lot of decisions on behalf of the user. The option is not easily found because I doubt many people will care about losing a few MBs of space for thumbnails, the people who do care can find out how to change it with a quick google search.

But if would like to see your suggested improvements introduced, you can try submitting them to developers via [Launchpad]("http://en.wikipedia.org/wiki/Launchpad_%28website%29"). It is possible there are good reasons behind the way it is set up now, or it could be that no-one has asked them to be changed before.

---

### Post by drewsus on 2011-01-31
And actually, the way that Windows handles it would take more system resources. The impact on the system is minimal, but it is still doing more. It is making sure that it does not have thumbnails for things that are no longer on system and that there are not relic thumbnails when you change them and so forth. I view this as being very low in terms of system resource usage on both OSes. 
And personally, I'd rather have all the thumbnails in one separate folder than in each individual folder. 
But that is just my opinion.

---

### Post by FreddieMacelvoy on 2013-02-06
As an additional data point I will say that my .thumbnails folder was 916MB and contained over 90,000 files.  I am still googling to see how to limit the total size of this folder, as this thread does not seem to say, despite one post alleging that it is limited to 512MB.

Regards,

Fred

---

### Post by wildmanne39 on 2013-02-06
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

