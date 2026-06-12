---
title: "Launch Application + alias"
date: 2010-04-26
forum: General Help
---

### Post by sombrancelha on 2010-04-26
Hello,

I've set some alias for bash, but, obviously, they only work on the terminal.

What I want to do is to launch some applications (Alt+F2) using such "alias" - I guess I'd have to define them somewhere else, but I don't know where.

Thank you

---

### Post by Seal Daemon on 2010-04-26
Create a symlink :)

```
ln -s <real-file> <link>
```

** If it involves something more than just a file name, a shell script would be the easiest way around this.

---

### Post by sombrancelha on 2010-04-26
I tried

```

ln -s /opt/google/chrome/google-chrome chrome

```

It runs fine when I do it trough the terminal (I've deleted the alias). But when I try trough Launch App (Alt+F2), gedit opens this file:

```

#!/bin/bash
#
# Copyright (c) 2009 The Chromium Authors. All rights reserved.
# Use of this source code is governed by a BSD-style license that can be
# found in the LICENSE file.

# Let the wrapped binary know that it has been run through the wrapper
export CHROME_WRAPPER="`readlink -f "$0"`"

PROGDIR="`dirname "$CHROME_WRAPPER"`"

case ":$PATH:" in
  *:$PROGDIR:*)
    # $PATH already contains $PROGDIR
    ;;
  *)
    # Append $PROGDIR to $PATH
    export PATH="$PATH:$PROGDIR"
    ;;
esac

# Always use our versions of ffmpeg libs.
# This also makes RPMs find the compatibly-named NSS3/NSPR symlinks.
LD_LIBRARY_PATH="$PROGDIR:$PROGDIR/lib:$LD_LIBRARY_PATH"
export LD_LIBRARY_PATH

export CHROME_VERSION_EXTRA="beta"

# We don't want bug-buddy intercepting our crashes. http://crbug.com/24120
GNOME_DISABLE_CRASH_DIALOG=SET_BY_GOOGLE_CHROME
export GNOME_DISABLE_CRASH_DIALOG

exec -a "$0" "$PROGDIR/chrome" "$@"

```

Also, there's another alias I've been using:

```

alias origin='env WINEPREFIX="/home/martin/.wine" wine "C:\Arquivos de programas\OriginLab\OriginPro75\Origin75.exe"'

```

which envolves Wine. I guess that would be the case of the script, right? What should it be and where should I save it?

---

