---
title: "Need a little hand with Xampp. Should be easy."
date: 2011-02-24
forum: General Help
---

### Post by Mr. ViC on 2011-02-24
So, I got this school work to do, to create some databases with MySQL using XAMPP and stuff, easy way as we're still in the beginning.

Now, I'm the only one in the whole class using Linux. And I'm getting some questions here.

I've installed XAMPP, configured it, seems to be working.

Now, I have these commands that the other guys with Windows could do with no problem, like:

```
mysql -u root
```

Then:

```
mysql -u "username" -p “database name”
```

You see where this is going. They can do that with no problem, but here on Ubuntu it's like:

```
fish: Unknown command “mysql”
The program 'mysql' can be found in the following packages:
 * mysql-client-core-5.1
 * mysql-cluster-client-5.1
Try: sudo apt-get install <selected package>
```

(yes, I'm using fish with the terminal, it's pretty and I like it)

So, I cd'ed to the folder where it should work:

```
root@ViTALiTY ~# /opt/lampp/lampp mysql -u root
Usage: /opt/lampp/lampp <action>

    start        Start XAMPP (Apache, MySQL and eventually others)
    startapache  Start only Apache
    startssl     Start only SSL support
    startmysql   Start only MySQL
    startftp     Start only ProFTPD

    stop         Stop XAMPP (Apache, MySQL and eventually others)
    stopapache   Stop only Apache
    stopssl      Stop only SSL support
    stopmysql    Stop only MySQL
    stopftp      Stop only ProFTPD

    reload       Reload XAMPP (Apache, MySQL and eventually others)
    reloadapache Reload only Apache
    reloadmysql  Reload only MySQL
    reloadftp    Reload only ProFTPD

    restart      Stop and start XAMPP
    security     Check XAMPP's security

    php5         Activate PHP5
    phpstatus    Which version of PHP is active?

    backup       Make backup file of your XAMPP config, log and data files
    panel        Starts graphical XAMPP control panel
```

And that's what it outputs.

Where and how should I use the commands in order for them to work? The teacher doesn't seem to know much about Linux either. But I'm not planning to use Windows for it, so...

Can anyone give me a hand here please?

---

### Post by gordintoronto on 2011-02-24
I'm surprised you are using xampp rather than Apache.

Start Software Center and search for mysql. Install the server and the client, maybe even administrator and query browser.

You will need to make some notes when you install mysql, so have pen and paper handy.

You'll probably need php at some point, might as well grab it while you're there.

---

### Post by Mr. ViC on 2011-02-26
Thank you for your reply, I got my problem solved. :)

---

