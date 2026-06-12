---
title: "Setting environment variables"
date: 2011-08-27
forum: General Help
---

### Post by talebinezhad on 2011-08-27
[B]Hello all 
i was trying to install prman and in the instructions manuals it explains how to set environment variables by using "setenv" command i tried to write it once again by "export" command and added this to my .bashrc :[/B]


export RMANTREE=/opt/pixar/RenderManProServer-13.5
export RMSTREE=/opt/pixar/RenderMan_Studio-1.0-Maya8.5
export RMSDOCTREE=/opt/pixar/docs/RMS-1.0
export RMANFB=it
export AW_LOCATION=/usr/aw
#export MAYA_LOCATION $AW_LOCATION/maya
#export MAYA_PLUG_IN_PATH  $RMSTREE/bin
#export MAYA_SCRIPT_PATH $RMSTREE/lib/mtor/resources
export XBMLANGPATH=$RMSTREE/lib/mtor/resources/%B
export LD_LIBRARY_PATH "$MAYA_LOCATION/lib:$RMSTREE/bin"
if ($RMSTREE == $RMANTREE) then
    export path = ($path $RMANTREE/bin)
else
    export path = ($path $RMSTREE/bin $RMANTREE/bin)
fi


[B]i know these lines contains errors but cant fix them i dont know how,anyone can help ?
the original instruction was :
[/B]
setenv RMANTREE /opt/pixar/RenderManProServer-13.5
 setenv RMSTREE /opt/pixar/RenderMan_Studio-1.0-Maya8.5
 setenv RMSDOCTREE /opt/pixar/docs/RMS-1.0
 setenv RMANFB it
 setenv AW_LOCATION /usr/aw
 setenv MAYA_LOCATION $AW_LOCATION/maya
 setenv MAYA_PLUG_IN_PATH  $RMSTREE/bin
 setenv MAYA_SCRIPT_PATH $RMSTREE/lib/mtor/resources
 setenv XBMLANGPATH "$RMSTREE/lib/mtor/resources/%B"
 setenv LD_LIBRARY_PATH "$MAYA_LOCATION/lib:$RMSTREE/bin"
 if ($RMSTREE == $RMANTREE) then
     set path = ($path $RMANTREE/bin)
 else
     set path = ($path $RMSTREE/bin $RMANTREE/bin)
 endif

**thank you.**

---

### Post by gmargo on 2011-08-27
To translate the CSH syntax for the 'if/else' into SH format, try this:
```

if [ "$RMSTREE" = "$RMANTREE" ] ; then
    PATH="$PATH:$RMANTREE/bin"
else
    PATH="$PATH:$RMSTREE/bin:$RMANTREE/bin"
fi

```

---

### Post by talebinezhad on 2011-08-30
Thank you gmargo its fixed now .:D

---

