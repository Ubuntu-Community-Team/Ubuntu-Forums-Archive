---
title: "Scripting basics and debugging"
date: 2011-08-24
forum: General Help
---

### Post by .Guest. on 2011-08-24
A basic `System information` script, modeled after this one:

```

#!/bin/bash

# system_page - A script to produce a system information HTML file

##### Constants

TITLE="System Information for $HOSTNAME"
RIGHT_NOW=$(date +"%x %r %Z")
TIME_STAMP="Updated on $RIGHT_NOW by $USER"

##### Functions

function system_info
{
    echo "<h2>System release info</h2>"
    echo "<p>Function not yet implemented</p>"

}   # end of system_info


function show_uptime
{
    echo "<h2>System uptime</h2>"
    echo "<pre>"
    uptime
    echo "</pre>"

}   # end of show_uptime


function drive_space
{
    echo "<h2>Filesystem space</h2>"
    echo "<pre>"
    df
    echo "</pre>"

}   # end of drive_space


function home_space
{
    # Only the superuser can get this information

    if [ "$(id -u)" = "0" ]; then
        echo "<h2>Home directory space by user</h2>"
        echo "<pre>"
        echo "Bytes Directory"
        du -s /home/* | sort -nr
        echo "</pre>"
    fi

}   # end of home_space



##### Main

cat <<- _EOF_
  <html>
  <head>
      <title>$TITLE</title>
  </head>
  <body>
      <h1>$TITLE</h1>
      <p>$TIME_STAMP</p>
      $(system_info)
      $(show_uptime)
      $(drive_space)
      $(home_space)
  </body>
  </html>
_EOF_

```

with a few more core utility commands including, `usr/bin/info`. The output file is a `.html` file. 

When run from the terminal, the cursor returns to the next line in the terminal, blinking.

When press `Ctr D` the normal terminal prompt returns `user@user:~$`, after this message:

```

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
info: Writing node (dir)Top...
info: Done.

```

The .html output file does load all of the information called by the script, the bug is the script does not end. It stops on pressing `Ctr D`.

How to stop script? How to debug?

Thanks for any help.

---

### Post by papibe on 2011-08-25
The code you are posting works fine. It would be more easy to make suggestions if you post the actual script that is generating the errors.

BTW. if the script hangs, you can stop it by pressing Ctrl+C (Control C).

Regards.

---

### Post by sisco311 on 2011-08-25
[http://mywiki.wooledge.org/BashGuide/Practices#Debugging](http://mywiki.wooledge.org/BashGuide/Practices#Debugging)

---

### Post by Habitual on 2011-08-25
Add ```
set -x
``` in the 2nd line of the script (under #!/bin/bash)

Then run the script in terminal, it will show you "more"

---

### Post by .Guest. on 2011-08-25
[quote=papibe]
The code you are posting works fine. It would be more easy to make suggestions if you post the actual script that is generating the errors.

BTW. if the script hangs, you can stop it by pressing Ctrl+C (Control C).

Regards.[/quote]
papibe, the script will be posted here. It is a simple `system information` script. The goal is for it to run and stop without errors, loops or force-quit by keys.

sisco311, bad link?

Habitual, thanks.

---

### Post by sisco311 on 2011-08-26
> **.Guest. said:**
> 

sisco311, bad link?



The link is good, but it seams that the site is down.

---

### Post by nothingspecial on 2011-08-26
> **sisco311 said:**
> The link is good, but it seams that the site is down.

:shock:

---

### Post by sisco311 on 2011-08-26
> **nothingspecial said:**
> :shock:

:)
pgas has a mirror:

[http://pgas.freeshell.org/mirror/wooledge/](http://pgas.freeshell.org/mirror/wooledge/)


@OP: try: [http://pgas.freeshell.org/mirror/wooledge/BashGuide.html#BashGuide.2BAC8-Practices.Debugging](http://pgas.freeshell.org/mirror/wooledge/BashGuide.html#BashGuide.2BAC8-Practices.Debugging)

---

### Post by .Guest. on 2011-09-15
What is the best way to release a script?

What should be included? 
README? 
The entire source code in this thread, in a post?
A new thread?
A web page for the script?

Thanks.

---

