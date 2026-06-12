---
title: "Irssi scripting"
date: 2010-01-31
forum: General Help
---

### Post by Kvothe on 2010-01-31
How would I go about making a printed variable in this script bold?
```
#!/usr/bin/perl -w

BEGIN{
use vars '$hook','$info';
eval q {
use Irssi;
};
$hook = !!$@;
}

sub np
{
$info = `rhythmbox-client --print-playing-format %ta\\ -\\ %at\\ -\\ %tt\\ -\\ "(%td)"`;
chop $info;
Irssi::active_win->command("/me is now playing: ".$info);
return 1;
}

if ($hook){
rb();
}else{
Irssi::command_bind('np', 'np')
}
```Source: [http://ubuntuforums.org/showthread.php?t=900937](http://ubuntuforums.org/showthread.php?t=900937)

---

### Post by Kvothe on 2010-01-31
No one?

---

### Post by Kvothe on 2010-01-31
So helpful.

---

