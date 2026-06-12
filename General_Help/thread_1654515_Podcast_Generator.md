---
title: "Podcast Generator"
date: 2010-12-28
forum: General Help
---

### Post by danbar on 2010-12-28
I'm trying to have a podcast generator. I already had some feedback in: [http://askubuntu.com/questions/19017/how-to-create-the-xml-file-for-podcasting](http://askubuntu.com/questions/19017/how-to-create-the-xml-file-for-podcasting)

frabjous has promised to provide more technical details. Many thanks!

---

### Post by frabjous on 2010-12-29
So I maintain a webpage for my friend's philosophical band, and I also do the podcast, which is registered through iTunes.

My friend sends me the MP3 of the new song. First, I make sure the ID3v2 tags (metadata) in the file are right. Next, I upload it to the webserver and make sure that's working.

I then update the XML file for the podcast RSS feed with a BASH script.

So suppose the (initially empty) podcast xml file (mine is named **rss.xml**) starts off looking like this:

```

<?xml version="1.0" encoding="utf-8"?>
 <rss xmlns:itunes="http://www.itunes.com/dtds/podcast-1.0.dtd" xmlns:atom="http://www.w3.org/2005/Atom" version="2.0">
 <channel>
 <atom:link href="http://PATH-TO-RSS/XML/FILE" rel="self" type="application/rss+xml" />
     <title>PODCAST TITLE</title>
     <link>http://PATH-TO-WEBPAGE</link>
     <description>DESCRIPTION OF PODCAST (SHORT)</description>
     <lastBuildDate>Mon, 27 Dec 2010 17:16:55 GMT</lastBuildDate>
     <language>en-us</language>
     <copyright>Copyright 2010 © WHOEVER</copyright>
     <itunes:subtitle>PODCAST SUBTITLE</itunes:subtitle>
     <itunes:author>PODCAST AUTHOR</itunes:author>
     <itunes:summary>PODCAST SUMMARY (LONGER)</itunes:summary>
     <itunes:owner>
         <itunes:name>PODCAST MAINTAINER</itunes:name>
         <itunes:email>maintainer@email.address</itunes:email>
     </itunes:owner>
     <itunes:image href="http://PODCAST-IMAGE-URL/something.jpg" />
     <itunes:category text="Category1" />
     <itunes:category text="Category2">
            <itunes:category text="Subcategory" />
     </itunes:category>
     
     <itunes:explicit>no</itunes:explicit>
 </channel>
 </rss>

```(You'll need to change that on your own; any text editor will do.)

I then make a template for a new item, below,, and save it as a text file **podcast.template** which looks like this:  (kk are my initials -- the kk-words are just placeholders for substitution using sed; I just needed to pick patterns that wouldn't occur naturally in the template):

```

    <item>
        <title>kksongtitlekk</title>
        <link>http://the.podcast.website/</link>
        <itunes:author>The Band Name</itunes:author>
        <description>kkpodcastdesckk</description>
        <itunes:summary>kkpodcastdesckk</itunes:summary>
        <enclosure url="kkurlkk" length="kkfilesizekk" type="audio/mpeg"/>
        <guid>kkurlkk</guid>
        <pubDate>kkcurrdatekk</pubDate>
        <itunes:duration>kkdurationkk</itunes:duration>
        <itunes:keywords>kkkeywordskk</itunes:keywords>
        <category>Podcasts</category>
        <itunes:explicit>no</itunes:explicit>
    </item>

```The script is called with a single argument: the URL of where I uploaded the song onto the webserver. The script then uses wget to fetch the song (make sure it actually exists and there's no typo!), reads the metadata with exiftool, and filesize of the song, makes a back-up of the old rss.xml file, and then creates a new one, adding the appropriate items into the slot. 

My script also expects a text files in the same folder named **description.txt** and **keywords.txt** which contain a description of the items you're adding and keywords for it. You can use any text editor to make this.

I'll add lots of comments to the script so perhaps you can see how it works.

Here it is. (I call this file addsong.sh -- make it executable with chmod +x addsong.sh):

```

#!/bin/bash
# read the URL of the MP3 from the command line argument
url=$1
# set the filename to the last part of the URL
file=$(echo $url | sed 's/.*\///')
# tell the user what (s)he's entered
echo "You entered URL $url"
# try to fetch the song with wget
if wget $url; then
    # if fetching succeeds
    echo "File found!"
    # get the song title from the file's metadata using exiftool
    songtitle="$(exiftool -S -Title $file | sed 's/Title: //' | sed -e 's/'"'"'/’/g')"
    # tell the user about it
    echo "the song title is $songtitle"
    # get the size of the file, tell the user about it
    filesize=$(stat -c %s $file)
    echo "the filesize is $filesize"
    # get the duration of the song using exiftool
    fileduration=$(exiftool -S -Duration $file | sed 's/Duration: //' | sed 's/ (approx)//')
    echo "the duration is $fileduration"
    # back-up the old rss.xml file
    mv rss.xml rss-old.xml
    # read the description from a file called description.txt
    podcastdesc=$(cat description.txt)
    # get the current date
    currdate=$(date -u -R | sed 's/\+0000/GMT/')
    # count the lines in the old xml file
    oldlength=$(wc -l < rss-old.xml)
    # figure out where to put new item, which should be three lines from bottom
    oldstop=$[oldlength-3]
    # get keywords
    keywords=$(cat keywords.txt)
    # update the date changed of the podcast by editing the old file
    cat rss-old.xml | sed "s/<lastBuildDate>.*<\/lastBuildDate>/<lastBuildDate>$currdate<\/lastBuildDate>/" | sed "$oldstop,$ d" > rss.xml
    # insert the new item, using sed to substitute what you need to
    cat podcast.template | sed "s|kksongtitlekk|$songtitle|g" | sed "s|kkpodcastdesckk|$podcastdesc|g" | sed "s|kkurlkk|$url|g" | sed "s|kkfilesizekk|$filesize|g" | sed "s|kkcurrdatekk|$currdate|g" | sed "s|kkdurationkk|$fileduration|g" | sed "s|kkkeywordskk|$keywords|g" >> rss.xml
    # recreate the last three lines of the podcast file
    echo "" >> rss.xml
    echo '    <itunes:explicit>no</itunes:explicit>' >> rss.xml
    echo '</channel>' >> rss.xml
    echo '</rss>' >> rss.xml
else
    echo "File not found on web!"
fi
exit


```You'll probably need to modify that according to your needs. It helps to know Bash, so I don't know how useful this will be if you don't. I'll give advice if I can, though. But it works great for me. I just enter:

./addsong.sh [http://url-of-song.com/something.mp3](http://url-of-song.com/something.mp3)

In the same folder with podcast.template, description.txt, keywords.txt and rss.xml and it does the rest.

You'll obviously need exiftool (sudo apt-get install libimage-exiftool-perl) -- I think everything else comes by default on Ubuntu.

---

### Post by danbar on 2010-12-29
Many thanks for your technical response.

---

### Post by Ck.asdf on 2013-04-17
I hate to resurrect a dead thread, but frabjous' information is highly helpful, minus some issues with the bash scripting.  First, while I'm familiar with making my way around the bash terminal, I've not done any scripting, and I'm not highly familiar with regex, and other advanced scripting things.  However, I'm okay at modifying other peoples' works.

The code below is my modification to frabjous' code, changing "kk" to "crk" (and changing the appropriate information in my podcast.template).  You'll notice the songtitle line is cut short compared to the original; I'm not sure what the deal is with all the single and double quotes, but it seemed to be fine to leave that portion off.  

```

#!/bin/bash
# read the URL of the MP3 from the command line argument
url=$1
# set the filename to the last part of the URL
file=$(echo $url | sed 's/.*\///')
# tell the user what (s)he's entered
echo "You entered URL $url"
# try to fetch the song with wget
if wget $url; then
    # if fetching succeeds
    echo "File found!"
    # get the song title from the file's metadata using exiftool
    songtitle=$(exiftool -S -Title $file | sed 's/Title: //')
    # tell the user about it
    echo "the song title is $songtitle"
    # get the size of the file, tell the user about it
    filesize=$(stat -c %s $file)
    echo "the filesize is $filesize"
    # get the duration of the song using exiftool
    fileduration=$(exiftool -S -Duration $file | sed 's/Duration: //' | sed 's/ (approx)//')
    echo "the duration is $fileduration"
    # back-up the old rss.xml file
    mv rss.xml rss-old.xml
    # read the description from a file called description.txt
    podcastdesc=$(cat description.txt)
    # get the current date
    currdate=$(date -u -R | sed 's/\+0000/GMT/')
    echo "current date is $currdate"
    # count the lines in the old xml file
    oldlength=$(wc -l < rss-old.xml)
    # figure out where to put new item, which should be three lines from bottom
    oldstop=$[oldlength-3]
    # get keywords
    keywords=$(cat keywords.txt)
    # update the date changed of the podcast by editing the old file
    cat rss-old.xml | sed "s/<lastBuildDate>.*<\/lastBuildDate>/<lastBuildDate>$currdate<\/lastBuildDate>/" | sed "$oldstop,$ d" > rss.xml
    echo "last build date changed"
    # insert the new item, using sed to substitute what you need to
    cat podcast.template | sed "s|crksongtitlecrk|$songtitle|g" | sed "s|crkpodcastdesccrk|$podcastdesc|g" | sed "s|crkurlcrk|$url|g" | sed "s|crkfilesizecrk|$filesize|g" | sed "s|crkcurrdatecrk|$currdate|g" | sed "s|crkdurationcrk|$fileduration|g" | sed "s|crkkeywordscrk|$keywords|g" >> rss.xml
    echo "inserted new podcast into xml file"
    # recreate the last three lines of the podcast file
    echo "" >> rss.xml
    echo '    <itunes:explicit>no</itunes:explicit>' >> rss.xml
    echo '</channel>' >> rss.xml
    echo '</rss>' >> rss.xml
    echo "recreated last three lines of podcast"
else
    echo "File not found on web!"
fi
exit

```



Now, when the "cat podcast.template ..." line gets run, 

When this line gets run, I get the error below:

> 
sed: -e expression #1, char 92: unterminated `s' command


Character 92 is around where the pipe is between "...desccrk" and "$pod..." in the code-snippet below:
sed "s|crkpodcastdesccrk|$podcastdesc|g"

I'm confused, though: this line doesn't use the "-e" switch.

---

### Post by overdrank on 2013-04-17
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

