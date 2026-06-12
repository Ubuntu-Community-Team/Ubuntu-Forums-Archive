---
title: "compiling gkrellm plugins"
date: 2006-05-28
forum: General Help
---

### Post by RaoulDuke on 2006-05-28
I've been unable to compile any gkrellm plugins and I finally just found that I must install gkrellm-devel in order to do so. 

However, I am now unable to find a anything but gkrellm-devel RPM's.

Any help will be greatly appreciated.

---

### Post by ranf on 2006-05-29
Usually -devel packages in Ubuntu are named <package>-dev. But I can't find something like that for Gkrellm specifically.

You could try to grab the build-dependencies for another gkrellm plugin and hope that's all you need for yours:
```
sudo apt-get build-dep gkrellmwireless
```

---

### Post by RaoulDuke on 2006-05-29
Thank You!

That's all I needed to do. I'm surprised I didn't find that anywhere while researching this. I apt-gettttted for gkrellmms, then it worked, now for the wireless!

---

