---
title: "Disk Quotas"
date: 2012-03-19
forum: General Help
---

### Post by kshep92 on 2012-03-19
Hi all,

I have a Rails app on my Ubuntu 11.10 installation that allows users to upload pictures. For each user, the app creates a new folder in the app's directory and puts each user's uploaded files in his respective folder.

My question is: Can I set a quota on each of the user folders that are created and adjust quotas as needed on a per-folder basis? If not, can I create a new file system or partition and set an option somewhere to limit the maximum size of folders created on that partition?

I want each user to be able to have a maximum of 10MB of space per account.

I'm open to anything btw, so if creating quotas aren't the best way then the next best thing will do as long as it achieves the same effect.

Thanks guys.

---

### Post by JC Cheloven on 2012-03-19
As far as I know, quotas apply to users. If each uploading person is logged in as a different user, then installing the quota package should be of help (or using quotactl from a program).

But probably the uploading people are not even logged in the system at all. In that case, I guess you should control the size of directories by means of a script (I understood you use ruby?), as a part of your whole application.

Please note: I never actually did something similar, so please take my words with some caution ;)

---

### Post by kshep92 on 2012-03-19
Thanks for the response.

Since I posted this message i've been doing some thinking and came up with the following proposed solution:


[LIST]
[*]For each file that is passed to the server, run a Ryby/Shell script that finds out how much space is left in the current user's file folder.
[*]Find out the size of the uploaded file
[*]Subtract the file size from the space_left variable
[*]If the result is positive, then save the file
[*]If the result is a negative number then throw an error and redirect or something
[/LIST]

This is what i'm thinking about, but I don't know how performance-friendly this method is. Still open to suggestions.

---

