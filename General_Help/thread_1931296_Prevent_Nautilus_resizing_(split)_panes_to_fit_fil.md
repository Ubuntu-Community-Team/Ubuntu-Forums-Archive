---
title: "Prevent Nautilus resizing (split) panes to fit filenames"
date: 2012-02-25
forum: General Help
---

### Post by Michael_K_Vegfruit on 2012-02-25
Since 11.10, Nautilus seems to resizing the filename column to fit long filenames, and resizing split panes likewise.  This then squeezes out the other pane on my tiny netbook screen.  Is there a way to stop it from doing this?  Either completely, or by limiting the column or pane to a maximum width?

-----

Edit, 26 February:

OK, googled some more and finally found the right search term to get an answer to this.  Briefly, running the following command in terminal will fix it:
```
gconftool-2 --type boolean --set /apps/nautilus/list_view/all_columns_have_same_width true
```There's a slightly more detailed explanation [here]("http://askubuntu.com/questions/70979/fixed-columns-width-in-nautilus")

---

