---
title: "Software Updates"
date: 2012-08-19
forum: General Help
---

### Post by clifford junior on 2012-08-19
When I download software from the Ubuntu Software Centre, is that software automatically updated when a newer version is released and added to the centre by the developer?

I know PPAs automatically update when you perform an update in the terminal, but what about the software from the Ubuntu Software Centre?

I can't seem to find any definite answer to this so any help would be appreciated.

Thank you.

---

### Post by Cheesehead on 2012-08-19
Yes and no.

A new release may be packaged by someone else instead of the upstream developer. Packaging can be different from developing. Many upstream projects, especially multi-platform projects, are quite happy to have a Ubuntu user willing to volunteer as a packager and maintainer.

The packager uploads the new version to the PPA right away. Those update whenever the PPA maintainer feels like it. That's wwhy PPAs are great for testing.

The Ubuntu Repos (main, restricted, universe, multiverse) are a snapshot for that release. They generally don't update. Instead, when you do a release upgrade semiannually, you move on to the next updated snapshot.

There are exceptions: Security updates, important bugfixes, and some regular updates (like Firefox) are regularly updated in the repos and pushed to users. Everything else -like a new upstream package release- waits for the next version of Ubuntu...

...but there's an exception to that, too. Pushing a new package release to the current version of Ubuntu is called *backporting*. There's a backports repository, and an Ubuntu Backporters team with upload rights to that repo.

---

