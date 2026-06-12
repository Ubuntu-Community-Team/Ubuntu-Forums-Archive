---
title: "www access denied"
date: 2010-10-29
forum: General Help
---

### Post by spindler on 2010-10-29
I want to install a website on my Ubuntu machine.  I have a lamp installed and I my domain name is pointing to the machine.

The problem I have is  I can only see the default index file.  index.html

It shows the text. 

IT WORKS!
This is the default web page for this server.
The web server software is running but no content has been added yet.

I was hoping to be able to add some content. I have a couple of problems.

1.  I cannot copy a new index file into the folder because I do not have  permission.  Does any one know how to work around this.   How do I load  files into the folder without having to disable the security 

2  I want to put many websites on the machine.  I think i need to create an index page for each website inside this folder.   I once read a document on this.  Does anyone know where this is.

3.  I would really like to have my websites accessible via FTP.  How do I  point to each individual site via ftp so I can upload the files  remotely specifically for each website.

---

### Post by eric_1982 on 2010-10-29
*1. I cannot copy a new index file into the folder because I do not have permission. Does any one know how to work around this. How do I load files into the folder without having to disable the security*

[B]have you tried to use the command-line with the sudo command?

Example: If you had a file called file2.html in a folder called websitefiles in your home directory (/home/username/websitefiles) you could copy like this

 sudo cp ~/websitefiles/file2.html /var/www/[/B]


*2 I want to put many websites on the machine. I think i need to create an index page for each website inside this folder. I once read a document on this. Does anyone know where this is.*
[B]
If you want to have one page that links to other directories you can just create a html with the links. If you want to have different sites with different domain names you will want to do some reading on virtual domains for apache. [/B]

[http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/](http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/)


*3. I would really like to have my websites accessible via FTP. How do I point to each individual site via ftp so I can upload the files remotely specifically for each website.*
[B]
Will multiple people be login in or just you?[/B]

---

### Post by Verbeck on 2010-10-29
try
```
sudo gedit /etc/apache2/sites-available/default
```in the file , change [B]
DocumentRoot /var/www [/B]to[B] DocumentRoot /link/to/a/folder/in/your/home/directory
[/B]
and[B]

<Directory /var/www/>[/B] to **<Directory /link/to/a/folder/in/your/home/directory/**>

it should solve the first issue

---

### Post by spindler on 2010-10-29
Hello Eric,

Thank you for your thoughts.   I am thinking about setting up a web hosting site.  So I will have many users accessing their websites.

I have not recently tried the sudo command.  I will give it a try and see if I can move files into the folder.

I have many domain names that point to my server.  So I want to use apache.  I did find a document that might help   [https://help.ubuntu.com/10.10/serverguide/C/httpd.html](https://help.ubuntu.com/10.10/serverguide/C/httpd.html).    I am just going through it now.

Yes I will have many users logging into the server.   I currently cannot access my site remotely via FTP.   I think I am having a problem with FileZilla...or a firewall some place.   I think maybe I set up the router with the wrong information.  Again I am looking into it.

---

### Post by SeijiSensei on 2010-10-29
[http://ubuntuforums.org/showpost.php?p=10016541&postcount=3](http://ubuntuforums.org/showpost.php?p=10016541&postcount=3)

---

