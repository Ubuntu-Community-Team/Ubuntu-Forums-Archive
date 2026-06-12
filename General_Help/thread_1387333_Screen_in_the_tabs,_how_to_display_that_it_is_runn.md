---
title: "Screen: in the tabs, how to display that it is running or waiting?"
date: 2010-01-21
forum: General Help
---

### Post by frenchn00b on 2010-01-21
Hello,

Into screen, some tabs in the taskbar are present. Some tabs (bash) are running some scripts and there is stuffs that are done, and in some other tabs : it is waiting... How to display if a tab is running a script or .. whatever compiling   or other case: waiting for user ?  man is not telling. 

Hoping that sbdy knows...
Best regards

```

# status
hardstatus alwayslastline "%{= Yk} %H %{= yk}%-Lw%{= kG}%50> %n%f* %t %{-}%+Lw%< %=  %{= yk} %l %{= Yk} %0c:%s %d/%m %{-}"

# add CPU idle/sustem/user/interrupt stats
backtick 100 5 5 tail -n 1 $HOME/.log
caption always '%{= kY} %200` %= %100` %='


bindkey ^[[1;5A prev
bindkey ^[[1;5B next
bindkey ^[[1;5D prev
bindkey ^[[1;5C next
bindkey ^N screen
bindkey ^[[1;2D prev
bindkey ^[[1;2C next

bindkey -k F1 prev
bindkey -k F2 next

```

---

