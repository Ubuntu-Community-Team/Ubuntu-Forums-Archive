---
title: "BitTorrent/FTP Client"
date: 2009-07-29
forum: General Help
---

### Post by Dead_$partan on 2009-07-29
I am looking for something similar to Bit Comet for Linux, in the sense of an all in one Bit Torrent client.  Bit Comet has a cool FTP client that gets downloads via FTP done in seconds as it seems to download the FTP file from several FTP servers at once.

I am using deluge as my bit torrent client but it doesnt seem to have this FTP functionality, is there any that does this for Linux?

---

### Post by hibliss on 2009-07-29
> **Dead_$partan said:**
> Bit Comet has a cool FTP client that gets downloads via FTP done in seconds as it seems to download the FTP file from several FTP servers at once.



Bitcomet sucks, and does not download from multiple FTP servers at once.

Nautilus can handle ftp addresses, or just use gftp, or one of the countless linux ftp clients.

Bitcomet may SEEM faster, but it is all in your head. FTP is FTP, the protocol is the same for every client, and speeds are dependent on the server you are downloading from.

---

### Post by x33a on 2009-07-29
if you want a good FTP client, go for filezilla. it doesn't support bittorrent, but it's really good for ftp transfers.

---

### Post by Dead_$partan on 2009-07-29
> **hibliss said:**
> Bitcomet sucks, and does not download from multiple FTP servers at once.

Nautilus can handle ftp addresses, or just use gftp, or one of the countless linux ftp clients.

Bitcomet may SEEM faster, but it is all in your head. FTP is FTP, the protocol is the same for every client, and speeds are dependent on the server you are downloading from.

I can understand why you say Bit Comet sucks and I do not use it anymore, but the FTP downloads is defo faster.  I have downloaded files via FTP using my web browsers standard built in ftp and compared using bit comet to download the same file.  Bit comet has downloaded the files at a rate of at least 500kbps, when you look at the download info it usually lists at least 5 ftp servers which it states it is pulling the file from.  I dont know how it works but I can confidently say it IS faster.  I used it for over a year when windows was my main OS so I have have had plenty of experience downloading files via FTP using this program.  The website states the following for FTP/HTTP downloads:

HTTP/FTP DownloadInnovative P2P Technology
**P2P downloading:** BitTorrent technology is integrated into HTTP/FTP download, with which BitComet automatically finds other clients and gets data from them to increase your download speed&#65292;without additional bandwidth usage of the HTTP server. [B]
Intelligent File Rename:[/B] [Automatic choose the best name for your download file]("http://wiki.bitcomet.com/Intelligent_File_Rename").
**Preview while Downloading:** [Preview of mp3, rmvb, wmv, and qt is available during downloading process]("http://wiki.bitcomet.com/Preview_while_Downloading").
**Multi-Mirror download**: Mirror servers are automatically found for the file being downloaded. Data from these servers are downloaded at the same time to increase download speed 300% or more. 
**Multi-Section download:** Files are split into several sections which are downloaded at the same time to increase the download speed up to 500% or more. 
**Multi-Language Support:** Multi-language web pages and encoded URLs can be correctly handled. [B]
Quick Resume[/B]: Stopped download tasks can be resumed from where they left off from both HTTP and FTP servers.

---

### Post by Elep.Repu on 2009-07-29
I like transmission for bittorrent.
Simple, and it's faster.

---

### Post by GoldenSun on 2009-07-29
> **Dead_$partan said:**
> I can understand why you say Bit Comet sucks and I do not use it anymore, but the FTP downloads is defo faster.  I have downloaded files via FTP using my web browsers standard built in ftp and compared using bit comet to download the same file.  Bit comet has downloaded the files at a rate of at least 500kbps, when you look at the download info it usually lists at least 5 ftp servers which it states it is pulling the file from.  I dont know how it works but I can confidently say it IS faster.  I used it for over a year when windows was my main OS so I have have had plenty of experience downloading files via FTP using this program.

I don't believe ftp can download in that fashion.  So either you don't know what you are looking at or it's actually just different trackers.  

I recommend filezilla as ftp and deluge for torrent.

If you don't like downloading stuff windows has built in ftp in command prompt.

---

### Post by Dead_$partan on 2009-07-29
> **GoldenSun said:**
> I don't believe ftp can download in that fashion.  So either you don't know what you are looking at or it's actually just different trackers.  

I recommend filezilla as ftp and deluge for torrent.

If you don't like downloading stuff windows has built in ftp in command prompt.

Maybe i dont but the things im downloading is device drivers and program .exe files from websites, the usual downloads that would trigger your browesers ftp client.  Bit Comet has a plugin that kciks in and handles the download and does it much faster.  From theirn website...

HTTP/FTP DownloadInnovative P2P Technology
**P2P downloading:** BitTorrent technology is integrated into HTTP/FTP download, with which BitComet automatically finds other clients and gets data from them to increase your download speed&#65292;without additional bandwidth usage of the HTTP server. [B]
Intelligent File Rename:[/B] [Automatic choose the best name for your download file]("http://wiki.bitcomet.com/Intelligent_File_Rename").
**Preview while Downloading:** [Preview of mp3, rmvb, wmv, and qt is available during downloading process]("http://wiki.bitcomet.com/Preview_while_Downloading").
**Multi-Mirror download**: Mirror servers are automatically found for the file being downloaded. Data from these servers are downloaded at the same time to increase download speed 300% or more. 
**Multi-Section download:** Files are split into several sections which are downloaded at the same time to increase the download speed up to 500% or more. 
**Multi-Language Support:** Multi-language web pages and encoded URLs can be correctly handled. [B]
Quick Resume[/B]: Stopped download tasks can be resumed from where they left off from both HTTP and FTP servers.

---

### Post by hibliss on 2009-07-29
If there are multiple servers available, you can utilize bandwidth from several of them, thus getting faster download speeds. Most things like drivers and publicly available files that would be hosted this way with multiple ftp mirrors would not be very large, or would also be available via Bittorrent (which generally utilizes your full available connection on Linux ISOs and similar files).

On the other hand, private ftps would not have this capability, because the files are not publicly hosted at multiple mirrors.

---

### Post by Dead_$partan on 2009-07-29
> **hibliss said:**
> If there are multiple servers available, you can utilize bandwidth from several of them, thus getting faster download speeds. Most things like drivers and publicly available files that would be hosted this way with multiple ftp mirrors would not be very large, or would also be available via Bittorrent (which generally utilizes your full available connection on Linux ISOs and similar files).

On the other hand, private ftps would not have this capability, because the files are not publicly hosted at multiple mirrors.

They are going to have multiple ftp servers to handle the various downloads from several people browising the website.  Any FTP file I have ever downloaded sing Bit Comet had listed at the very elast 3 FTP servers that its downloading from, more often its around 5 tho and i get between 300-500kbps.  No matter how u look at it its far better than the usual speeds I get using standard ftp clients.  So now we understand each other a little better, is there one that I can use for linux that would give me these capabilities?

---

### Post by hibliss on 2009-07-29
I am not aware of any, and I am going to say I don't think there are any. I is looked at as rude to abuse mirrors in this way.

ftp transactions for things hosted in the way you explain are generally volunteer mirrors or sponsored mirrors. Either way, it is a misappropriation of someone else's bandwidth to exploit multiple mirrors for the same download. 

Bitcomet was previously an unethical bittorrent client, and it looks as if it is an unethical ftp client as well.

---

### Post by Dead_$partan on 2009-07-30
I don't think it's abusing mirrors, from what I understand it downloads a small chunk from each FTP server so that would be lowering the data transfer per server.  I can see the issue with torrents using bit comet but im not so sure how it handles FTP is a bad thing.

---

