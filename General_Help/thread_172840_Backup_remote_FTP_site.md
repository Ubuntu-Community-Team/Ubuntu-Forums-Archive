---
title: "Backup remote FTP site"
date: 2006-05-09
forum: General Help
---

### Post by jonnymccullagh on 2006-05-09
I need to make daily backups (cron) of a website via FTP (syncronising or copying down changed files only). I previously did this on windows using a great program called PyrobatchFTP.
Now I am on Kubuntu I was wondering if anyone had any tips. I have looked at rsync but my remote server (website/ftp) is a windows server and locally I am running kubuntu and the tutorials I have read on rsync seem to imply that both need to be linux boxes.
I would like something where I can specifiy the FTP address, FTP user, FTP pass, remote folder, local folder
I'm sure there must be something out there that can do this?
Thanks in advance as always,
jonny

---

### Post by MJN on 2006-05-09
Rsync can live quite happily on a Windows box - check out 'cwrsync' at [http://www.itefix.no/phpws/]("http://www.itefix.no/phpws/").

I'm a great supporter of rsync - I use it more and more now that I'm getting more familiar with it. Like many things once you start getting to grips with how it works it becomes a very powerful tool.

I installed the Windows version above just to try it out and can confirm it works, however my main experience is with running it on Linux so I can't comment on any differences that there might be (I'm think in terms of file ownership whilst stored on a Windows machine...?)

Mathew

---

### Post by jonnymccullagh on 2006-05-10
I followed your link but I was a little reluctant to start installing this stuff on the Windows server just in case I messed anything up. But as I was reading I read about lftp
So I found a tutorial and installed it and found that I could backup up my website by FTP using lftp to my Linux desktop.

I created a text file with the following:
debug -o /home/jonny/documents/backups/debugoutput.txt 3
lcd /home/jonny/documents/backups
open 111.222.333.444
user myftpusername myftppassword
mirror /  /
exit

I could then run this script using lftp with the following command:
lftp -f /home/jonny/documents/backups/lftpscriptfile.txt

I made a shell script with this command in it to run by Cron but this is my next problem. 
I went to KCron and added the program as /path/to/mysell.sh as a Cron job but it isn't running this program when I choose 'Run Now' - and I don't get any feedback from KCron as to the success or otherwise or even a last run date/time.
If I run the shell script manually it works but not from within KCron so can anyone help me with this?
thanks,
jonny

---

