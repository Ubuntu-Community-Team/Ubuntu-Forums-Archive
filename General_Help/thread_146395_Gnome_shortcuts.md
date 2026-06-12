---
title: "Gnome shortcuts"
date: 2006-03-18
forum: General Help
---

### Post by tenn on 2006-03-18
In kde you can press F4 that opens a terminal in the directory you are currently in, is there a way to set this or similar for gnome.

---

### Post by audax321 on 2006-03-18
Don't know about setting a keyboard shortcut, but you can use this script:

```

#!/usr/bin/env python

# Open command prompt in a single selected directory
# or otherwise in current dir

# Put this (executable) file in ~/.gnome2/nautilus-scripts/
# Then right click a directory or anywhere in current dir window
# to get the scripts->command_prompt_here menu option

# This has been tested on nautilus 2.2 and 2.4

def nautilus_script_display_error():
    """This is a general error message display for nautilus scripts"""
    import sys
    #errors_fd,errors_name=tempfile.mkstemp() #This not available until python 2.3
    errors_name=os.tmpnam()
    errors_fd=file(errors_name,"w")
    etype, emsg, etb = sys.exc_info()
    errors_fd.write('line '+str(etb.tb_lineno)+': '+str(etype)+': '+str(emsg)+'\n')
    errors_fd.write('\n$PWD: %s' % os.getcwd())
    errors_fd.write('\nsys.argv: %s' % str(sys.argv[1:]))
    for var in os.environ:
        if var.startswith("NAUTILUS_"):
            errors_fd.write("\n%s: %s" % (var,os.environ[var].replace('\n',"\\n")))
    errors_fd.close()
    pid = os.fork()
    if pid == 0:
        cmd = ["zenity", "--text-info", "--filename=%s" % errors_name, "--title=error", "--width=640", "--height=220"]
        os.execvp(cmd[0],cmd)
    os.waitpid(pid,0)
    os.unlink(errors_name)

import os
import urllib, urlparse
try:
    home_dir=os.environ["HOME"]

    # An alternative to below could be:
    #   1. get where we are (CURRENT_URI (file://, trash:, x-nautilus-desktop:///))
    #   2. use argv to see if 1 selected dir under that?
    dir_to_open=""
    selected=os.environ["NAUTILUS_SCRIPT_SELECTED_URIS"].split("\n")[:-1]
    #Note getting SELECTED_URIS rather than SELECTED_FILE_PATHS as later
    #is not set when ~/Desktop and ~/.Trash selected??
    if len(selected) == 1:
        uri_bits=urlparse.urlparse(urllib.unquote(selected[0]))
        if uri_bits[0] == "file":
            dir_to_open=uri_bits[2]
        elif uri_bits[0] == "x-nautilus-desktop":
            if uri_bits[2] == "///trash":
                dir_to_open=home_dir+'/.Trash'
            elif uri_bits[2] == "///home":
                dir_to_open=home_dir+'/Desktop'
        if not os.path.isdir(dir_to_open):
            dir_to_open=""
    if not dir_to_open: #we didn't select 1 directory so open current dir
        current_uri=os.environ["NAUTILUS_SCRIPT_CURRENT_URI"]
        uri_bits=urlparse.urlparse(urllib.unquote(current_uri))
        if uri_bits[0] == "file":
            dir_to_open=uri_bits[2]
        elif uri_bits[0] == "x-nautilus-desktop":
            dir_to_open=home_dir+'/Desktop'
        elif uri_bits[0] == "trash":
            dir_to_open=home_dir+'/.Trash'
    shell_cmd=["gnome-terminal", "--working-directory=%s"%dir_to_open]
    os.execvp(shell_cmd[0],shell_cmd)
except:
    nautilus_script_display_error()

```

I didn't write this script. I got it from some website. Basically just save it as 'Open Terminal Here' (make sure the permissions allow it to execute) and put it in /home/<username>/.gnome2/nautilus-scripts

Then when you right-click in a folder and go to the Scripts menu in Nautilus, you can open a terminal there.

---

### Post by Xian on 2006-03-18
[QUOTE=audax321]Don't know about setting a keyboard shortcut, but you can use this script:
[/QUOTE]

You don't have to go through all that.
Just install the nautilus-open-terminal package in the Universe repo.

---

### Post by tenn on 2006-03-18
Thanks both, to easy. I have been wondering how to do something similar I find small things like that very useful.

---

