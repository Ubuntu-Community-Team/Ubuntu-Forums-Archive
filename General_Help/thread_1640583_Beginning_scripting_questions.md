---
title: "Beginning scripting questions"
date: 2010-12-08
forum: General Help
---

### Post by Curse on 2010-12-08
Hey y'all, I have two questions.

First, I'm wondering why my script isn't working. When I first made it, it worked, but now I get an error.

Here is the script:
```
#!/bin/bash

# make_page - A script that produces an HTML file

title="My System Information for $HOSTNAME"
RIGHT_NOW=$(date +"%x %r %Z")
TIME_STAMP="Updated on $RIGHT_NOW by $USER"

cat <<- _EOF_
        <HTML>
        <HEAD>
                <TITLE>
                $title $HOSTNAME
                </TITLE>
        </HEAD>

        <BODY>
        <H1>$title</H1>
        <P>$TIME_STAMP
        </BODY>
        </HTML>
_EOF_

```

Now, for example, typing
make_page > page.html

gives me:

bash: make_page: command not found

Even though it was working at first. 

I'm also curious why it makes a new file for my own scripts with a ~ at the end of the name.

i.e. typing ls gives me both make_page and make_page~

I've noticed it does this with every one I've changed.
I added a little bit to .bashrc and now there's also .bashrc~

Help?

---

### Post by dcstar on 2010-12-08
> **Curse said:**
> 
.........
Now, for example, typing
make_page > page.html

gives me:

bash: make_page: command not found

........

```
./make_page > page.html
```

---

### Post by Curse on 2010-12-08
Thank you.

Now I have run into a .gvfs issue... just running my script :/

This is the script now 

```
#!/bin/bash

# make_page - A script that produces an HTML file

##### Constants

title="My System Information for $HOSTNAME"
RIGHT_NOW=$(date +"%x %r %Z")
TIME_STAMP="Updated on $RIGHT_NOW by $USER"

##### Functions

function system_info
{
	echo "<H2>System release info</H2>"
	echo "<P>Function not yet implemented</P>"

}


function show_uptime
{
	echo "<H2>System uptime</H2>"
	echo "<PRE>"
	uptime
	echo "</PRE>"

}


function drive_space
{
	echo "<H2>Filesystem space</H2>"
	echo "<PRE>"
	df
	echo "</PRE>"

}


function home_space
{
if [ $(id -u) = "0" ]; then
	echo "<H2>Home directory space by user</H2>"
	echo "<PRE>"
	echo "Bytes Directory"
	du -s /home/* | sort -nr
	echo "</PRE>"
else
	echo "You must be the Superuser to run this script" >&2
fi
}


##### Main

cat <<- _EOF_
	<HTML>
	<HEAD>
		<TITLE>
		$title $HOSTNAME
		</TITLE>
	</HEAD>

	<BODY>
	<H1>$title</H1>
	<P>$TIME_STAMP</P>
	$(system_info)
	$(show_uptime)
	$(drive_space)
	$(home_space)
	</BODY>
	</HTML>
_EOF_
```

Why would this try to use .gvfs?

---

### Post by HurricaneHarry on 2010-12-08
.gvfs is used when you try find the /home sizes with du

---

### Post by Curse on 2010-12-08
> **HurricaneHarry said:**
> .gvfs is used when you try find the /home sizes with du

Is it ok to remove .gvfs? I found this regarding the file:

"A solution to remove .gvfs , odd directory:

#umount /home/useraccount/.gvfs
#find . -inum 554009 -exec rm{} \;

After that,

#rm -rf .gvfs

"

I just did the first step, unmounting it and it is working now. Of course, I can't mount it again ( sudo mount /home/user/.gvfs), but does that damage anything?

And what is up with the copies of my scripts with the ~ after them?

---

### Post by wannabegeek on 2010-12-08
the tilde is an automatic backup made when you saved or closed your editor...
It's saved me a few times but annoying to look at...there's  a way to not list those *.*~  files.

try man ls

---

### Post by Curse on 2010-12-09
> **wannabegeek said:**
> the tilde is an automatic backup made when you saved or closed your editor...
It's saved me a few times but annoying to look at...there's  a way to not list those *.*~  files.

try man ls

Makes sense, thank you!

---

