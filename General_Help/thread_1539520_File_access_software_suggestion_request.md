---
title: "File access software suggestion request"
date: 2010-07-26
forum: General Help
---

### Post by studiogrynn on 2010-07-26
I tried searching here and via Google for an answer, but failed at every attempt. Perhaps I am just un aware of the correct class of software I should be searching for.

We are looking for an easy to use solution that will allow us to post files on our web/ftp server and provide the client ready and controlled access to those files for download. 

Here is how I envision it working. 
- we place file on protected server
- we send client an email with a link to download the file
- client gets access to his files and his alone via this link

Many of our users will not be familiar with FTP clients, so something web based might be the best option for the noobs, and setting up ftp accounts for every client would be major effort. 

Thoughts and ideas?

---

### Post by lloyd_b on 2010-07-26
> **studiogrynn said:**
> I tried searching here and via Google for an answer, but failed at every attempt. Perhaps I am just un aware of the correct class of software I should be searching for.

We are looking for an easy to use solution that will allow us to post files on our web/ftp server and provide the client ready and controlled access to those files for download. 

Here is how I envision it working. 
- we place file on protected server
- we send client an email with a link to download the file
- client gets access to his files and his alone via this link

Many of our users will not be familiar with FTP clients, so something web based might be the best option for the noobs, and setting up ftp accounts for every client would be major effort. 

Thoughts and ideas?

Is there some reason you can't just email the actual file to the client as an attachment?  That's the only simple method for doing what I think you want...

Any method that is intended to restrict it so that a client can access his and only his files is going to require a lot of work, similar to setting up separate FTP accounts for each client.  There's no way around this.

There's no need for a special FTP client to access files from an ftp server - most any web browser can do so, via "ftp://..." URLs.  They can even access files that are on an ftp server that requires username and password authentication - see [here]("http://www.timeatlas.com/5_minute_tips/general/connecting_to_ftp_sites_with_a_web_browser") for some examples.

Lloyd B.

---

### Post by studiogrynn on 2010-07-26
Lloyd,
Thanks for the input.
Email is too limiting in file size. While some of the files will be under 20 megs, some of the recipients may be using aol or another ISP that recompress the file.

I'll look at the suggested link - thank you.

---

