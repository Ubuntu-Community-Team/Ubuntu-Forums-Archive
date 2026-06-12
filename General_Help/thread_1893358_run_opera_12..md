---
title: "run opera 12.?"
date: 2011-12-10
forum: General Help
---

### Post by Matrix01 on 2011-12-10
i downloaded opera 12.
how do i run this?

 [opera-next-12.00-1191.i386.linux.tar.xz]("http://snapshot.opera.com/unix/kisskiss_12.00-1191/opera-next-12.00-1191.i386.linux.tar.xz")    05. Linux 32-bit - XZ compressed tar, with install script (all distros)

---

### Post by idoitprone on 2011-12-10
Open up the commandline


```
cd /to/the/directory/ 
```unpack the file from either command line or file brower
```
cd opera-next-12.00-1191.i386.linux

```to run opera
```
./opera-next
```
or run it though your file brower
To install opera

```
sudo ./install
```You have an choice where to install you code
type```
 ./install --help
``` to view you options
```

    --text          Select plain-text user interface.

    --unattended    Ask no questions. Implies --text.
                    The --prefix option becomes mandatory.

    --quiet         Ask no questions and don't show progress.
                    Implies --text.

    --prefix /P     Specify installation directory. Opera will be
                    installed into /P/bin, /P/share and /P/lib.

    --user          Install for the current user. Default for non-root.
                    Alias for --prefix /home/food/.local.

    --system        Install for everybody. Default for root.
                    Alias for --prefix /usr/local.

    --name N        Use N for package name. Must either be "opera" or
                    begin with "opera-". Names of installed files and
                    directories will contain this string in place of
                    "opera". This allows to install several
                    versions of Opera side by side. The default is
                    "opera-next".

    --suffix S      Obsolete. Same as --name opera-S.

    --force         Ignore all kinds of errors and try to continue.

    --repackage R   Special mode for package maintainers. Extract files
                    into the staging directory R as if it were the
                    installation prefix, but prepare them to be
                    installed under the actual prefix. In this mode, no
                    finalizing actions, such as registration of menu
                    entries, are performed. Sanity checks are disabled.
                    Implies --unattended.

    --version       Show Opera version.

    --help          Show this message.
```

---

### Post by stinkeye on 2011-12-10
Not sure how you install the compressed file.
You can install opera-next through [**_[COLOR="DarkRed"]http://deb.opera.com/[/COLOR]_**]("http://deb.opera.com/")
After you install an Opera Debian package manually for the first time, it will add the opera repository to your sources.

ie I installed the latest opera stable release by dowloading the deb file from [**_[COLOR="darkred"]HERE[/COLOR]_**]("http://www.opera.com/browser/download/")
Now if I wish I can install opera-next through synaptic or the software center.Advantages...automatic updating.
Opera-Next installs a separate pre-release version with a white icon and
can be run alongside the stable version.

---

### Post by Spyderkid on 2011-12-10
install the .deb file from the Opera website.

Then double click on the .deb file and it should install

---

### Post by Matrix01 on 2011-12-12
[ATTACH]208948[/ATTACH]

copied and pasted your code, and
output is like this,
i am not sure opera was installed.
opera is downloaded in download file.


> **idoitprone said:**
> Open up the commandline


```
cd /to/the/directory/ 
```unpack the file from either command line or file brower
```
cd opera-next-12.00-1191.i386.linux

```to run opera
```
./opera-next
```or run it though your file brower
To install opera

```
sudo ./install
```You have an choice where to install you code
type```
 ./install --help
``` to view you options
```

    --text          Select plain-text user interface.

    --unattended    Ask no questions. Implies --text.
                    The --prefix option becomes mandatory.

    --quiet         Ask no questions and don't show progress.
                    Implies --text.

    --prefix /P     Specify installation directory. Opera will be
                    installed into /P/bin, /P/share and /P/lib.

    --user          Install for the current user. Default for non-root.
                    Alias for --prefix /home/food/.local.

    --system        Install for everybody. Default for root.
                    Alias for --prefix /usr/local.

    --name N        Use N for package name. Must either be "opera" or
                    begin with "opera-". Names of installed files and
                    directories will contain this string in place of
                    "opera". This allows to install several
                    versions of Opera side by side. The default is
                    "opera-next".

    --suffix S      Obsolete. Same as --name opera-S.

    --force         Ignore all kinds of errors and try to continue.

    --repackage R   Special mode for package maintainers. Extract files
                    into the staging directory R as if it were the
                    installation prefix, but prepare them to be
                    installed under the actual prefix. In this mode, no
                    finalizing actions, such as registration of menu
                    entries, are performed. Sanity checks are disabled.
                    Implies --unattended.

    --version       Show Opera version.

    --help          Show this message.
```

---

### Post by Matrix01 on 2011-12-12
i am on 32 bit netbook.
is this gonna work?

> **stinkeye said:**
> Not sure how you install the compressed file.
You can install opera-next through [**_[COLOR=DarkRed]http://deb.opera.com/[/COLOR]_**]("http://deb.opera.com/")
After you install an Opera Debian package manually for the first time, it will add the opera repository to your sources.

ie I installed the latest opera stable release by dowloading the deb file from [**_[COLOR=darkred]HERE[/COLOR]_**]("http://www.opera.com/browser/download/")
Now if I wish I can install opera-next through synaptic or the software center.Advantages...automatic updating.
Opera-Next installs a separate pre-release version with a white icon and
can be run alongside the stable version.

---

### Post by Matrix01 on 2011-12-12
i checked out website.
it's opera 11.60.
do u mean, first, install this opera 11.60,
and upgrade to 12.?
, 
> **stinkeye said:**
> Not sure how you install the compressed file.
You can install opera-next through [**_[COLOR=DarkRed]http://deb.opera.com/[/COLOR]_**]("http://deb.opera.com/")
After you install an Opera Debian package manually for the first time, it will add the opera repository to your sources.

ie I installed the latest opera stable release by dowloading the deb file from [**_[COLOR=darkred]HERE[/COLOR]_**]("http://www.opera.com/browser/download/")
Now if I wish I can install opera-next through synaptic or the software center.Advantages...automatic updating.
Opera-Next installs a separate pre-release version with a white icon and
can be run alongside the stable version.

---

### Post by Alwimo on 2011-12-12
> **Matrix01 said:**
> i checked out website.
it's opera 11.60.
do u mean, first, install this opera 11.60,
and upgrade to 12.?
,
12 is available as an alpha from their website.
[http://www.opera.com/browser/next/](http://www.opera.com/browser/next/)

---

### Post by stinkeye on 2011-12-12
> **Matrix01 said:**
> i checked out website.
it's opera 11.60.
do u mean, first, install this opera 11.60,
and upgrade to 12.?
,

What  I mean is once you install opera 11.60 stable release,
you will able to install
**opera-next** 12 through the software centre.
It won't upgrade opera 11.60.
It installs a separate version of opera for testing called **opera-next**.

If you only want to install opera-next you can add the opera repository manually.

Open Software Sources and click on the **Other Software** tab.
Click on the add button and copy and paste this into the box.
```
deb http://deb.opera.com/opera/ stable non-free
```
Click the add source button then close Software Sources.


To install the signing  key for the repository, copy and paste this into the terminal...(make sure you include the [COLOR="Red"]dash [/COLOR] at the end when copying.
```
wget -qO - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add [COLOR="red"]-[/COLOR]
```


Now in the terminal update your sources...
```
sudo apt-get update
```


Now you can either open the ubuntu software centre and search for opera-next and install (It may not show up)
or
to install through the terminal...
```
sudo apt-get install opera-next
```

---

### Post by digithal on 2011-12-12
If you don't wanna add Opera's repository, just do this:
```
wget http://snapshot.opera.com/unix/kisskiss_12.00-1191/opera-next_12.00.1191_i386.deb
sudo dpkg -i opera-next_12.00.1191_i386.deb
```

First command will download the compiled deb package. The second will install it.

---

### Post by Matrix01 on 2011-12-12
[ATTACH]208954[/ATTACH]

software center looks like this.
where is add button?

> **stinkeye said:**
> What  I mean is once you install opera 11.60 stable release,
you will able to install
**opera-next** 12 through the software centre.
It won't upgrade opera 11.60.
It installs a separate version of opera for testing called **opera-next**.

If you only want to install opera-next you can add the opera repository manually.

Open Software Sources and click on the **Other Software** tab.
Click on the add button and copy and paste this into the box.
```
deb http://deb.opera.com/opera/ stable non-free
```Click the add source button then close Software Sources.


To install the signing  key for the repository, copy and paste this into the terminal...(make sure you include the [COLOR=Red]dash [/COLOR] at the end when copying.
```
wget -qO - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add [COLOR=red]-[/COLOR]
```
Now in the terminal update your sources...
```
sudo apt-get update
```
Now you can either open the ubuntu software centre and search for opera-next and install (It may not show up)
or
to install through the terminal...
```
sudo apt-get install opera-next
```

---

### Post by Matrix01 on 2011-12-12
[ATTACH]208955[/ATTACH]
downloaded opera 12.
it does not run.

> **Alwimo said:**
> 12 is available as an alpha from their website.
[http://www.opera.com/browser/next/](http://www.opera.com/browser/next/)

---

### Post by Matrix01 on 2011-12-12
[ATTACH]208957[/ATTACH]
done.
that was smooth operation.
thank you.
how to make opera default browser?

> **digithal said:**
> If you don't wanna add Opera's repository, just do this:
```
wget http://snapshot.opera.com/unix/kisskiss_12.00-1191/opera-next_12.00.1191_i386.deb
sudo dpkg -i opera-next_12.00.1191_i386.deb
```First command will download the compiled deb package. The second will install it.

---

### Post by digithal on 2011-12-12
[QUOTE=Matrix01]how to make opera default browser?[/QUOTE]
Use:
```
update-alternatives --config x-www-browser
```
You will see something like this:
```
There are 3 alternatives which provide `x-www-browser'.

  Selection    Alternative
-----------------------------------------------
            1    /usr/bin/firefox-8.0
*+          2    /usr/bin/chromium
            3    /usr/bin/opera

Press enter to keep the default[*], or type selection number:
```
Type the number showing before /usr/bin/opera and press enter.

---

### Post by stinkeye on 2011-12-12
> **Matrix01 said:**
> [ATTACH]208954[/ATTACH]

software center looks like this.
where is add button?

Well you seem to have it installed now but for your info
**Software Sources** is not the **ubuntu software centre **
Type sources in the dash search.
It can also be accessed from the software centre > menu > Edit.

---

### Post by Matrix01 on 2011-12-13
[ATTACH]209031[/ATTACH]

two of opera 12.,  auto or manual?


> **digithal said:**
> Use:
```
update-alternatives --config x-www-browser
```You will see something like this:
```
There are 3 alternatives which provide `x-www-browser'.

  Selection    Alternative
-----------------------------------------------
            1    /usr/bin/firefox-8.0
*+          2    /usr/bin/chromium
            3    /usr/bin/opera

Press enter to keep the default
[*], or type selection number:
```Type the number showing before /usr/bin/opera and press enter.

---

### Post by Matrix01 on 2011-12-13
[ATTACH]209033[/ATTACH]

found it,
thank you.

> **stinkeye said:**
> Well you seem to have it installed now but for your info
**Software Sources** is not the **ubuntu software centre **
Type sources in the dash search.
It can also be accessed from the software centre > menu > Edit.

---

### Post by gradinaruvasile on 2011-12-13
The simplest way to do this is by just downloading the .deb version, and double click. It will automatically add repos and stuff.

BTW the default browser can be "default" in more than 1 way - there is gnomes or xfce's settings (preferred applications or something), the mentioned x-www-browser etcetc. Some programs may still use other settings though in xfce (mainly they get it from the Gnome settings).

---

### Post by Matrix01 on 2011-12-14
[ATTACH]209138[/ATTACH]
puzzeled,

typed 0, 
* is already on opera,

and typed 2, error message showed up.

> **digithal said:**
> Use:
```
update-alternatives --config x-www-browser
```You will see something like this:
```
There are 3 alternatives which provide `x-www-browser'.

  Selection    Alternative
-----------------------------------------------
            1    /usr/bin/firefox-8.0
*+          2    /usr/bin/chromium
            3    /usr/bin/opera

Press enter to keep the default
[*], or type selection number:
```Type the number showing before /usr/bin/opera and press enter.

---

### Post by stinkeye on 2011-12-14
Use sudo
```
sudo update-alternatives --config x-www-browser
```

---

### Post by Matrix01 on 2011-12-16
is opera default browser?
[ATTACH]209184[/ATTACH]

> **stinkeye said:**
> Use sudo
```
sudo update-alternatives --config x-www-browser
```

---

### Post by stinkeye on 2011-12-16
> **Matrix01 said:**
> is opera default browser?
[ATTACH]209184[/ATTACH]
Looks like it.
Open up one of your progams with a link in the about/info section, and test.

---

### Post by Matrix01 on 2011-12-16
when i click desktop short cut of ubuntu forum,
firefox opens this forum.

??

> **stinkeye said:**
> Looks like it.
Open up one of your progams with a link in the about/info section, and test.

---

### Post by stinkeye on 2011-12-16
I am not familiar with using the **sudo update-alternatives --config x-www-browser** command.

In 11.10 unity I just go to
system settings > system info > default applications

---

