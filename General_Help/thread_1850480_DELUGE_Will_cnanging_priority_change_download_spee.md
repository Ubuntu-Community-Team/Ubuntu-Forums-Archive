---
title: "DELUGE: Will cnanging priority change download speed?"
date: 2011-09-26
forum: General Help
---

### Post by Bramkaandorp on 2011-09-26
I have been wondering this for some time:

Whenever I change priority on some files in a torrent download (such as songs from Jamendo), it seems like the overall speed drops a little. This is even more apparent when I switch the priority of a file to "don't download".

It isn't equally prominent in every download, but I do notice it regularly enough to start questioning it.


So, is there anything to it?

---

### Post by Bramkaandorp on 2011-09-27
Bump

---

### Post by Cas07 on 2011-10-16
If you are talking about individual file priorities then yes. For reference it is the same as [piece priorities]("http://www.rasterbar.com/products/libtorrent/manual.html#piece-priority-prioritize-pieces-piece-priorities") and in Deluge we have set the values as: Normal = 1, High = 5 and Highest = 7.

---

### Post by Bramkaandorp on 2011-10-16
> **Cas07 said:**
> If you are talking about individual file priorities then yes. For reference it is the same as [piece priorities]("http://www.rasterbar.com/products/libtorrent/manual.html#piece-priority-prioritize-pieces-piece-priorities") and in Deluge we have set the values as: Normal = 1, High = 5 and Highest = 7.

I was specifically talking about the overall download speed of a torrent being affected by changing the priority of one of the files in that torrent.

Thanks for chipping in though.

---

### Post by lovinglinux on 2011-10-16
> **Bramkaandorp said:**
> I was specifically talking about the overall download speed of a torrent being affected by changing the priority of one of the files in that torrent.

Thanks for chipping in though.

Yes. Speed of your torrent depends on how many peers you connect and the speed of the peers, among other factors. Not all peers have all pieces of all files, so when you stop a particular file inside a multi-file download, some users will inevitable be disconnected or stop sending such pieces to you and overall speed decreases. It should regain speed later, when it connects to more peers with the pieces of active files.

---

### Post by Bramkaandorp on 2011-10-17
> **lovinglinux said:**
> Yes. Speed of your torrent depends on how many peers you connect and the speed of the peers, among other factors. Not all peers have all pieces of all files, so when you stop a particular file inside a multi-file download, some users will inevitable be disconnected or stop sending such pieces to you and overall speed decreases. It should regain speed later, when it connects to more peers with the pieces of active files.

That explains it. I see the exact thing you describe. Now that I know the underlying reasons for it, I can stop worrying.

Thanks.

---

### Post by lovinglinux on 2011-10-17
> **Bramkaandorp said:**
> That explains it. I see the exact thing you describe. Now that I know the underlying reasons for it, I can stop worrying.

Thanks.

You are welcome. Please mark the thread as solved using the Thread Tools menu.

---

### Post by Bramkaandorp on 2011-10-17
> **lovinglinux said:**
> You are welcome. Please mark the thread as solved using the Thread Tools menu.

Done.

---

