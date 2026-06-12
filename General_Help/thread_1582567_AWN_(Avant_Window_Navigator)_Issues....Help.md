---
title: "AWN (Avant Window Navigator) Issues....Help?"
date: 2010-09-26
forum: General Help
---

### Post by Llama Drama on 2010-09-26
Okay, so I downloaded the AWN package. I looked up instructions to install it and it says to open up the file synaptic manager and type in avant_window_navigator into the search box but whenever I type it in I get no results. The package is located in my downloads folder after downloading it through Firefox... I'm completely new to Ubunut and would really appreciate some help getting this installed. Thanks in advance!

---

### Post by realzippy on 2010-09-26
..type:

avant-window-navigator

in synaptic's search.
Further questions AWN:
[http://wiki.awn-project.org/index.php?title=Main_Page](http://wiki.awn-project.org/index.php?title=Main_Page)

---

### Post by sikander3786 on 2010-09-26
Whenever you need to install software on Ubuntu, first of all check in the repositories, same software might be available there and if installed from repositories, it also supports updates.

To use the repositories either go to Software Center under Applications or Synaptic Package Manager under System > Administration or install it from terminal by using apt-get or aptitude.

Search Software Center for Avant Windows Navigator and click install. Thats it.

---

### Post by coffeecat on 2010-09-26
If you open Synaptic and highlight any line under 'package' in the main pane, and then start typing what you think is the package name, it will go to it. By the time you have typed A-V-A-N, it will have found it for you. Useful if you don't know the exact syntax or spelling.

When using the search facility in Synaptic, use just one word - 'avant' should find it. Or use Ubuntu Software Centre. Again 'avant' in the search should find it easily.

You can discard the downloaded package - it's not needed.

---

### Post by Llama Drama on 2010-09-26
> **coffeecat said:**
> If you open Synaptic and highlight any line under 'package' in the main pane, and then start typing what you think is the package name, it will go to it. By the time you have typed A-V-A-N, it will have found it for you. Useful if you don't know the exact syntax or spelling.

When using the search facility in Synaptic, use just one word - 'avant' should find it. Or use Ubuntu Software Centre. Again 'avant' in the search should find it easily.

You can discard the downloaded package - it's not needed.

Hmm... well you see I did what you said and typed the entire name in the search bar and nothing showed up. I still dont understand why it's not showing up... Could it be that my internet isn't hooked up yet? If that has anything to do with it....??:confused::confused::confused::confused:

---

### Post by sikander3786 on 2010-09-27
Avant Windows Navigator is in the Universe Repos. Are Universe repos enabled on your system?

```

sudo apt-get update

```

```

sudo apt-get install avant-window-navigator

```

And if apt can't find the package, post the output of

```

cat /etc/apt/sources.list

```

---

### Post by coffeecat on 2010-09-27
> **Llama Drama said:**
>  Could it be that my internet isn't hooked up yet? If that has anything to do with it....??

Yes. All the package managers need what is called metadata before they can display available packages from the repositories. You need to hook up to the internet, open Synaptic and click on the Reload button. After that you will be able to find avant or whatever else is listed in the metadata that was just downloaded. And, as sikander3786 pointed out, you need the Universe repository enabled for avant. A new installation of Ubuntu normally has Universe enabled by default but it doesn't hurt to check this. In Synaptic, Settings > Repositories , and under Ubuntu Software tab see if the Community maintained (universe) line is ticked.

---

### Post by Llama Drama on 2010-09-27
Thanks! I will try and get my wireless card working then try the above suggestions.

---

