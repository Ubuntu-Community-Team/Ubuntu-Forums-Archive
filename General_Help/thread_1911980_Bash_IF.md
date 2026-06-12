---
title: "Bash IF"
date: 2012-01-19
forum: General Help
---

### Post by Kodeine on 2012-01-19
Salutations!

So I've done very little shell scripting in bash. I've been tried to get a bare basic if function going but I'm unable to. Basically I have two separate hot-keys to change the unity launchers display mode. One to set it to always show (nice when switching between windows alot) and one to dodge windows (nice when just using one application for a long time like browsing the web, so the launcher disappears). Feel free to use them! But instead of having two separate ones Id like a if statement that said if the 'launcher_hide_mode' is set to zero. then set it to two. If it's set to two then set it to zero.

Could someone please concocted this for thi?

Always show```
bash -c 'gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0'
```
Dodge windows```

bash -c 'gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 2'
```

---

### Post by mutley89 on 2012-01-19
I'm not familliar with gconftool, but from the man page you can get the current value of something with "gconftool-2 --get".  Is this what you are wanting to do: ```
 #!/bin/bash
if [[ $(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode") -eq 2 ]]  
then
    gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0 
else
    gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 2 
fi 
```The $(...) gets the output of the command inside it.  If you just used the command on it's own the [[ would use the exit status of the command, which would be 0 assuming no errors.

---

