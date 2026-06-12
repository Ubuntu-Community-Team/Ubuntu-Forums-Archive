---
title: "structure and privileges"
date: 2011-07-28
forum: General Help
---

### Post by allegrauser on 2011-07-28
I am totally new at this. The most experience I have had is installing mysql on a Mac. I setup a ubuntu server yesterday, I was impressed by how easy it was. I was able to connect with Filezilla via sftp. It logs me into a directory which has my username, but I guess the web folder is var/www. 

I am confused about the structure. I am setting this up as a development server. I do most of my hosting on ICDsoft. Their structure when I log in, is a private folder for scripts. Then there is the www directory which contains the sub domains which has the www sub domain directory. I would like to be able to have my server setup like this, but I am not sure the best way to do it.

Secondly I have found these command to give me permission to write to my var/www folder
sudo usermod -g www-data [username]
sudo chown -R www-data:www-data /var/www
sudo chmod -R 775 /var/www

This allows me to edit files in /var/www, so I copied a directory into it, however I can't rename that directory using Filezilla. What could be wrong?

Is there some where that gives an over all view of the files structure and how Ubuntu works with out  readying for a day?

---

### Post by allegrauser on 2011-07-28
Ok scratch the permission problem.

---

