---
title: "I think ive got a L.A.M.P lump for a brain!"
date: 2006-04-13
forum: General Help
---

### Post by dgrafix on 2006-04-13
Hello, 
I want to set up a dummy webserver on my lan to develop my webpage offline, and dont havea clue about apache and php (except from a client point of view). Ive installed apache2 and can access localhost (or 192.168.1.2 from my laptop) but i cant get php to work. i installed php5 but some where i read this was not good and to use php4 because of stability or something, and was reccommending a lib file not in the universe.

Basically is there a few sets of instructions on getting this working. every guide ive found so far goes into a complete essay on making, de-tar-ing etc(as usual](*,) ). What i mean is, because synaptic does this, i dont know exactly how much synaptic does before i have to go manual and start finding files to edit them.

I think i need a babybook:rolleyes:  on "this is apache, do this, this is php,perl & mysql, stick em 'here' and tell 'that' about them" specifically for deb/ubuntu and not linux in general?

Anyone got one, mabe titled 'Dans first trip to serverville'

I have since removed all modules i installed releated to apache and php and want to start from scratch.

---

### Post by jlhughes on 2006-04-13
Check out: 

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

This is an integrated package that installs Apache2, PHP5, mySQL, phpMyAdmin and an FTP server in an integrated package.  Everything is preconfigured. It even includes a script to secure the server.  (The only thing the Linux version lacks that the Windows version has is a mail server.)

---

### Post by dgrafix on 2006-04-14
Thanks :D  

Sounds like exactly what im after.

---

### Post by oscar on 2006-04-14
I prefer using the official ubuntu packages that get the necessary security updates and bugfixes automatically.
As far as I am aware all you need to do is open up a terminal and:
```
sudo apt-get install apache2 libapache2-mod-php5 mysql-server mysql-client
```
Those are the only packages you need and their dependencies are handled automatically.
The basic configuration should be done for you and you can start immediately, I am pretty sure I did.

That xampp looks easy but it installs a lot of things that aren't officially supported by the ubuntu people and you might not want anyway.
If you find you want something extra, open up synaptic and search for it.
For perl:
```
sudo apt-get install libapache2-mod-perl2
```
Python:
```
sudo apt-get install libapache2-mod-python
```

If you have problems with the ubuntu packages or configuration you can ask people here.

---

### Post by Gaia on 2006-04-14
hi,

I also want to set up a dummy webserver and have done what you have suggested ( using the Ubuntu packages ). But i can't seem to get my mySQL to work correctly.

I tried seeing the version to test to see if it worked and i get this

> 
melissa@blk-224-211-250:~$ mysqladmin version
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'melissa@localhost' (Using password: NO)'


Thanks!

---

### Post by oscar on 2006-04-14
Gaia, I get the same, I dont use mysqladmin.
try:
```
mysql -u root -p
```
and entering your password, if your installation is right it should work.
```
quit
```
quits and you get back to the normal bash terminal.
I will have a look at mysqladmin now
[EDIT]
Your command is wrong, you need:
```
mysqladmin -u user -p version
```
where user is your username, root to start with, the password should be your normal password.
The mysql manual for installation does use the command you tried but ubuntu sets more up for you than just the files, including passwords.

---

### Post by dgrafix on 2006-04-16
what is postfix?

and what is the difference between internet site and internet site with smarthost.


Ive managed to start apache now, but im trying a small simply hello world php script and its not working

---

### Post by oscar on 2006-04-18
to check apache visit:
[http://localhost/](http://localhost/) in your browser, you should get a default apache test page.
To write a test php script simply put:
> <?php
echo "Hello World";
?>
in a file, such as test.php, in /var/www
To test if this works visit:
[http://localhost/test.php](http://localhost/test.php)

---

