---
title: "Repository and Pkg's"
date: 2012-08-22
forum: General Help
---

### Post by UltimateCat on 2012-08-22
I have never been to a repository but I understand from reading a lot of documentation it's wise to only get pkg's from the Linux repositories in accordance with your distro.

I've learned how to use the terminal to:
```
apt-get install <packagename>

```
And I know how to install the .deb packages.

Once I'm in a repository; how do I obtain a package?

---

### Post by drmrgd on 2012-08-22
You don't really manually get a package from a repository per se.  Instead, the addresses for repositories are added to your sources list, and either (from terminal), running
```
 sudo apt-get update
``` 
followed by 
```
sudo apt-get install <package>
``` 
or from the Software Center opening, searching for, and clicking install for packages will retrieve and install that package.  

If you're looking at a repository that is not a part of your sources list (i.e. you find a repository PPA and want to get a package from it), you can either add the source to your list via the terminal:

```
sudo add-apt-repository <address of the repository> 
```

after which you should update the cache again:```


sudo apt-get update
```

And then install your package as above.  If you prefer the Software Center, you need to click on Edit > Software Sources, and under the "Other Software" tab, add the new repository.  

Here is the Community Documentation for Repositories that might help clear up some confusion:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Hope that helps!

---

### Post by UltimateCat on 2012-08-24
drmrgd:

I wrote down your entire post. This way I have it and can repeat the process for the future packages I may want.  Now I'm not confused-

Thanks for the link so I can do some reading.

---

