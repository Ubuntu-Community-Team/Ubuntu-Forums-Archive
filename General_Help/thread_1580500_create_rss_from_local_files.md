---
title: "create rss from local files"
date: 2010-09-23
forum: General Help
---

### Post by dbrenha on 2010-09-23
Hi all
i needed a way to create a rss file like this one to use with [cooliris]("http://cooliris.com"):
```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
      <rss version="2.0" xmlns:media="http://search.yahoo.com/mrss/"
      xmlns:atom="http://www.w3.org/2005/Atom">
      <channel>
          <title>Feed title</title>
          <description>Feed Description</description>
          <link>http://www.example_url.com</link>
          <item>
               <title>img_001</title>
               <media:description>img_001</media:description>
               <link>pl_images/img_001.jpg</link>
               <media:thumbnail url="http://example.com/pl_thumbs/img_001.jpg"/>
               <media:content url="http://example.com/pl_images/img_001.jpg"/>
          </item>
          <item>
               <title>img_002</title>
               <media:description>img_002</media:description>
               <link>pl_images/img_002.jpg</link>
               <media:thumbnail url="http://example.com/pl_thumbs/img_002.jpg"/>
               <media:content url="http://example.com/pl_images/img_002.jpg"/>
          </item>
      </channel>
      </rss>
```
the problem is that i have lots of files to do it by hand, so i thought that maybe there was an easier way with a script or something.
Anyone can help?

---

