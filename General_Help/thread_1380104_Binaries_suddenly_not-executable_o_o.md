---
title: "Binaries suddenly not-executable o_o"
date: 2010-01-13
forum: General Help
---

### Post by Tuxedo Mask on 2010-01-13
Greetings,

For the past few months, the following script was working fine for me; it allows me to open up Irfanview via Wine for browsing images, and even gave me the benefit of allowing the images to open in the program by double-clicking them:

```

#!/bin/bash
EXECUTE_STRING=$HOME"/.wine/drive_c/Program Files/IrfanView/i_view32.exe"
ROOT_DRIVE_MAPED_TO="z:"
WindowsFileName=${ROOT_DRIVE_MAPED_TO}`echo "$1" | sed 's/\//\\\/g'`
"$EXECUTE_STRING" "$WindowsFileName"

```

Starting yesterday, however, running this script would give me a "cannot execute binary file" error. I did install a bunch of updates last night (I'd been away for a few weeks, so they'd piled up), so I suppose that COULD account for it. This error also occurs if I just try to run what's in $EXECUTE_STRING alone, so it's not a permissions issue with the script.

I'm running Jaunty at the moment (2.6.31-16-generic-pae #53-Ubuntu) and can provide any other specs as needed. Thanks!

---

