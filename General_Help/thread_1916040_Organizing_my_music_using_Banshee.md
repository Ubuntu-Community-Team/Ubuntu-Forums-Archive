---
title: "Organizing my music using Banshee"
date: 2012-01-27
forum: General Help
---

### Post by Welly Wu on 2012-01-27
I own an ASUS N61JV-X2 notebook PC with Crucial 8 gigabytes of DDR3 1,066 MHz SDRAM and an Intel 2nd Generation 34nm MLC NAND FLASH X25-M 160 gigabyte Solid State Drive. I also have a Seagate FreeAgent Desk 1.5 terabyte external hard disk drive with USB 2 and I have a Kingston DataTraveler HyperX 128 gigabyte Super Speed USB 3 thumb drive. I performed a custom installation of Ubuntu 10.04.3 64 bit LTS using full disk encryption with LUKS/LVM (AES-CBC mode 256 bits SHA-256). I also use TrueCrypt to protect my Seagate and Kingston (AES-XTS mode 256 bits SHA-512).

I installed all of the optional components for Banshee and I do not have a problem with them. I am using Banshee to import my 1,100+ CDs and I am converting them to .FLAC lossless audio files. I store my .FLAC files on my Seagate hard drive into a folder named Music.

Normally, Banshee is configured so that my .FLAC files are saved onto the root directory on my Seagate hard drive, but I move them into my Music folder for better organization. Now, I can not play any music because I moved the location of each CD from the root directory to the Music folder.

I want to tell Banshee to look into my Music folder to store my .FLAC files in the future when I purchase new CDs and I want it to play from the Music folder when I want to listen to music.

How do I fix this problem?

I know that this must be a simple problem to solve, but I just installed Ubuntu 10.04.3 64 bit LTS and I just upgraded to Ubuntu 11.10 64 bit less than three days ago. I consider myself new to Ubuntu and I never really used Banshee extensively, but I am a competent GNU/Linux user. Please help me out if you can. I would really appreciate finer control over Banshee and my Music folder along with all of its sub-directories that represent individual artists and albums containing .FLAC files.

Thank you.

---

### Post by ajgreeny on 2012-01-27
If I understand you right, all you need to do is go to banshee > Edit > Preferences > Source Specific tab and there you can set your own choice of the folder where you store your music.  See screenshots.

---

### Post by Welly Wu on 2012-01-27
Thanks for that tip. I finally figured out how to use Banshee. I am playing my Aimee Mann CD through Banshee now and it is configured to search the Music folder on my TrueCrypt protected Seagate FreeAgent Desk 1.5 terabyte external hard disk drive. It works. I like Banshee a lot because it is easy to use and there are a ton of additional features that can be added and it allows me to convert my massive 1,100+ CD library to .FLAC lossless audio files.

---

### Post by Welly Wu on 2012-01-27
Now, I have another small problem that I need help to solve. Originally, Banshee would display the album cover along with the artist or band's name next to it. There would be rows and columns of albums displayed. I only see a text list of the artist, album title, name of the song, and the time for each song. I installed all of the optional components to Banshee in the Ubuntu Software Center and then I lost the ability to view my albums in alphabetical order as album covers.

How do I restore the ability to see album covers arranged in alphabetical order into columns and rows in Banshee?

---

### Post by Welly Wu on 2012-01-27
I solved my problem by myself. I just had to show the browser to get it back to the original look and feel within Banshee.

---

### Post by ajgreeny on 2012-01-27
Great,  can you go to Thread Tools menu at the top of this thread and mark as "Solved" please.

---

