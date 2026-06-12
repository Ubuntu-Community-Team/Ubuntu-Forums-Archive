---
title: "MPD/MPC Media Key Conditionally Previous Track"
date: 2012-06-16
forum: General Help
---

### Post by HiImTye on 2012-06-16
here's the bash script I wrote for MPD/MPC to use for my media key : 'audio previous' (previous track).
what it does: check the progress of the current song. if it's more than 5 seconds, restart the track. if it's more than 5 seconds, move to the previous track.

mpcPrevSong.sh
```
test=$(mpc | grep -Eo '[0-9]+:[0-9][0-9]/' | sed 's|\([0-9].*\):\([0-9][0-9]\)/|\1\2|')
if [ "$test" -ge 5 ]; then
 mpc seek 0
else
 mpc prev
fi
```

make sure it's executable. to set your media key to it, open 'keyboard' and then go to the shortcut tab and on the left, select 'Custom Shortcuts'. click the '+' button and then enter the path to your bash script you just saved in 'command' and call it whatever you want. once it's done, click where it says 'disabled' then press your media key. should work (if not try restarting). screenshot of settings screen:
[ATTACH]219804[/ATTACH]

---

