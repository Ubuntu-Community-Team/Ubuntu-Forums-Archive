---
title: "HOWTO: Work-around to re-index messages in Thunderbird"
date: 2012-01-24
forum: General Help
---

### Post by grumpypants on 2012-01-24
For a while I've been wondering how to force Thunderbird to re-index messages. I just discovered a round-about solution using Thunderbird 9 and Thunderbird Conversations ([https://addons.mozilla.org/en-US/thunderbird/addon/gmail-conversation-view](https://addons.mozilla.org/en-US/thunderbird/addon/gmail-conversation-view)).  When you first install Thunderbird Conversations it re-indexes your  messages. It also happily provides a way to repeat this on demand.

Tools -> Add-Ons -> Extensions -> Thunderbird Conversations  -> Preferences -> Start the setup assistant -> Apply changes

If you click Review changes before clicking Apply changes, you'll see that the following are checked:

[LIST]
[*]Make sure Global Search and Indexer is enabled.
[*]Re-index messages containing attachments as well as all Mozilla bugmail.
[/LIST]
After doing so you can monitor progress with Tools -> Activity Manager

p.s. Originally posted to [http://ubuntuforums.org/showpost.php?p=11637339&postcount=8](http://ubuntuforums.org/showpost.php?p=11637339&postcount=8), copied here by request.

---

