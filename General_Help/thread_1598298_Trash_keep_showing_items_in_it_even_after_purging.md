---
title: "Trash keep showing items in it even after purging"
date: 2010-10-16
forum: General Help
---

### Post by heldmar on 2010-10-16
Hello,

I'm using Ubuntu 10.04.

I recently modified the nautilus to show the trash icon as it didn't come by default on the Desktop.

I have a problem because the trash keeps showing items in it. When I put my mouse over it it keeps saying "6 items", however, when I open the trash it is totally empty.

I have googled and read a lot in this and other forums and haven't found a solution. I even did a 

```

sudo find / -name "Trash"

```

And couldn't find anything that let me fix this.

Has anyone faced this same issue and fixed it?

---

### Post by coffeecat on 2010-10-16
The location of trash is ~/.local/share/Trash, where ~ = your home folder and .local is a hidden folder. Press ctrl-H in your Nautilus home folder to reveal it.

You'll find three folders in Trash. If you can't see what has gone wrong, you can delete them all and they will be regenerated when you next use trash.

---

### Post by heldmar on 2010-10-16
> **coffeecat said:**
> The location of trash is ~/.local/share/Trash, where ~ = your home folder and .local is a hidden folder. Press ctrl-H in your Nautilus home folder to reveal it.

You'll find three folders in Trash. If you can't see what has gone wrong, you can delete them all and they will be regenerated when you next use trash.

Thanks. I did that before but it didn't work for me (the .Trash folder you mention just was not there).

Still, I found what was the problem: I was using Vuze (Torrents client) and as I deleted few torrents using Vuze, while I had it opened the trash was filled. Once I closed Vuze, the trash just showed '0 items', so basically it was Vuze's trash.

---

### Post by coffeecat on 2010-10-16
> **heldmar said:**
> the .Trash folder you mention just was not there.

I didn't mention a ".Trash" folder. There is no .Trash folder so I'm not surprised it wasn't there.

:wink:

[I]Yesterday upon the stair,
[/I][I]I met a man who wasn&#8217;t there.
[/I]*He wasn&#8217;t there again today.*[I]
Oh, how I wish he&#8217;d go away.[/I]

(William Hughes Mearns)

---

