---
title: "Search Unity lenses via the command line"
date: 2012-09-20
forum: General Help
---

### Post by RayDeCampo on 2012-09-20
The subject says it all: how can I search a Unity lens using the command line?  This would be useful, e.g., when ssh-ing into a machine.

For example, if I know I can get to the software center by searching for 'software' in the application lens but I don't know the command line for the software center it would be useful to be able to run the lens search via the command line and get results.  (For those with poor reading comprehension: I know the software center command is software-center.)

I swear I saw this on a blog somewhere in my travels but I can't find it now...

---

### Post by drmrgd on 2012-09-20
Not sure if this is what you're thinking / trying to do or not, but the BASH shell (the default in most Ubuntu installs) supports tab completion.  So, if you're not quite sure the package you want to run, you can type the first few letters of it, and then hit the tab key to autocomplete.  If you don't get an immediate result, it may mean that there is more than 1 result to complete what you've typed.  So, you can either hit the tab key again to list all the possible entries, or enter a few more letters and try tab again.  So, for example, if you wanted to launch Google Chrome from the command line, but didn't quite know the correct package name, you could type:

```
goog <hit tab key>
```

that will fill in the rest of the word google.  However, when you hit enter, you'll get an error about that package not being installed.  Hitting tab twice, will show (on my system anyway)google-chrome and googletalk-call.  Now I know that the correct package name is google-chrome, and I can either type the rest of the correct name, or add in the hypen and 'c' followed by a tab to fill the rest in.  

You can also use the 'apropos' command to get package names based on search criteria.  So, for example, if you wanted something software related, you could run 'apropos software', which on my system returns the following (I'm on Kubuntu, which does not have the software center - I think this might return Software Center on your system though):

```
$ apropos software
bjam (1)             - software build tool
fsf-funding (7gcc)   - Funding Free Software
gsignal (3)          - software signal facility
ImageMagick (1)      - is a free software suite for the creation, modification and display of bitmap images.
software-properties-kde (1) - Software Sources List editor
ssignal (3)          - software signal facility
```

Again, not sure if this is what you're looking for.  Hope that helps, though.

---

### Post by RayDeCampo on 2012-09-20
Thanks drmrgd for the reply.  Unfortunately that is not what I am looking for.  I am well aware of those tricks.  I am specifically looking for a way to invoke the same search you get via the unity dash lens.

---

### Post by drmrgd on 2012-09-20
Oh, I think I understand what you want to do now.  You essentially want to use the terminal to launch a Unity lens search.  I was thinking you wanted to search for packages using the commmand line in the same way you'd use Unity's lens search. The SSHing part threw me as I interpreted that as you'd be in a CLI only environment (which is a poor assumption!). 

Unfortunately, though, I'm on Kubuntu and don't know the specifics of how the Unity Lens search is invoked.  Sorry about that!

---

