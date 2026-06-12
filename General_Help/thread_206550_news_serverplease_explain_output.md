---
title: "news server/please explain output"
date: 2006-06-30
forum: General Help
---

### Post by lex1 on 2006-06-30
I have contacted my news server i am also going to be a news server
and i want to know or have a simple explaination of the output from the mail client suck. does not matter if you do not use suck, just a simple explaination of what the output infers.


lex1



lex1@xstation:~$ suck news.zen.co.uk -bp -hl localhost -c -i 0 -M -n
Attempting to connect to news.zen.co.uk
Using Port 119
Official host name: news.zen.co.uk
Address: 212.23.3.119
Connected to news.zen.co.uk
200 Zen Internet NNRP lovejoy.zen.co.uk Service Ready (posting ok)
200 Zen Internet NNRP lovejoy.zen.co.uk Service Ready (posting ok)
Skipping Line: #comp.os.linux.announce -1
Skipping Line: #comp.security.announce -1
Skipping Line: #gnu.announce -1
news.announce.newusers - 1 articles 4567-4567
news.newusers.questions - 1 articles 674435-674435
Elapsed Time = 0 mins 0.24 seconds
2 Articles to download
Deduping Elapsed Time = 0 mins 0.00 seconds
Deduped, 2 items remaining, 0 dupes removed.
Processing History File Elapsed Time = 0 mins 0.00 seconds
Processed history, 0 dupes removed
Total articles to download: 2
6543 Bytes received in 0 mins 0.21 secs, BPS = 31363.2
Closed connection to news.zen.co.uk
Posting Messages to localhost
Article Rejected, deleting: <01-welcome.txt.1151064300@presby.edu> - 437 Unwante
d newsgroup "news.announce.newusers"
Article Rejected, deleting: <nnq.44a3f915$1@darkstar> - 437 Unwanted newsgroup "
news.newusers.questions"
2 Messages Posted
Elapsed Time = 0 mins 0.08 seconds
Cleaning up after myself
/etc/suck/sucknewsrc: Permission denied
Moving newsrc to backup: Permission denied
lex1@xstation:~$

---

