---
title: "How to have quotes for wallpaper explained."
date: 2010-08-05
forum: General Help
---

### Post by jpmelos on 2010-08-05
Hello, everyone.

I like to read quotes a lot (I can spend a few hours in the Internet browsing random sites of quotes easily! :D). So, I've been wanting to put quotes for my wallpaper instead of images, and I want the quote to change periodically.

I looked for some software that would do that (write text for wallpaper instead of using an image), but I couldn't find it. So I figured a way to do that:

Using Conky and setting up a black wallpaper, I can simulate that behavior.

Conky executes a line of command that extracts a random line from a file and displays it on the screen. That file has a quote per line. The Conky is placed right in the center of the screen.

I'm using Conky 1.0.8.0 (from the Ubuntu repositories).

Using the following .conkyrc:

```
alignment middle_middle
background true
format_human_readable
use_xft
xftfont Arial:size=30
no_buffers yes
update_interval 1
double_buffer
no_buffers yes
max_text_width 0

TEXT
${execi 600 random_line /home/jpmelos/quotes}
```
This way, the quote will stick around for 10 minutes and then will be replaced another one, random. You may need to modify this configuration file depending on your screen resolution.

Using the following script for random_line:

```
#!/bin/bash

counter=$(wc -l < $1)
counter=$(($(($RANDOM%$counter))+1))
cat $1 | head -n $counter | tail -n 1 | fold -s -w50
```
Just put that in a file, name the file random_line and do

```
sudo mv random_line /usr/bin/random_line
sudo chmod +x /usr/bin/random_line
```
And here is the quotes file I use:

```
Don't let yesterday take up too much of today. -- Will Rogers
Don't let your victories go to your head, or your failures go to your heart. -- Unknown
Some people want it to happen, some wish it would happen, others make it happen. -- Michael Jordan
As you grow older, you'll find that the only things you regret are the things you didn't do. -- Zachary Scott
It is all right letting yourself go, as long as you can get yourself back. -- Mick Jagger
Prove who you are and they will accept who you are exactly. -- Unknown
Service to others is the rent you pay for your room here on Earth. -- Muhammad Ali
You can't change the wind, but you can set your sails. -- Billie Joe Armstrong
A loving heart is the beginning of all knowledge. -- Thomas Carlyle
Opportunities multiply as they are seized. -- Sun Tzu
Better to do something imperfectly than to do nothing perfectly. -- Robert Schuller
Success doesn't make you and failure doesn't break you. -- Zig Ziglar
The difference between genius and stupidity is that genius has its limits. -- Albert Einstein
People rarely succeed unless they have fun in what they are doing. -- Dale Carnegie
If you understand life, you must be misinformed. -- Paulo Coelho
Two great talkers will not travel far together. -- Spanish Proverb
If you smile when no one else is around, you really mean it. -- Eleanor Roosevelt
Goodbye without reasons is the most painful one. Love without reasons is the most beautiful one. -- Dhanti Praspani
Most of us can read the writing on the wall; we just assume it&#8217;s addressed to someone else. -- Ivern Ball
Adopt the pace of nature: her secret is patience. -- Ralph Waldo Emerson
Superior men are modest in speech but exceed in actions. -- Confucius
The question isn&#8217;t who is going to let me; it&#8217;s who is going to stop me. -- Ayn Rand
A friend is one of the nicest things you can have, and one of the best things you can be. -- Douglas Pagel
Don&#8217;t practice until you get it right. Practice until you can&#8217;t get it wrong. -- Lewis Carroll
Love your enemy, it will scare the hell out of them. -- Mark Twain
The best way to cheer yourself up is to cheer someone else up. -- Mark Twain
Formal education will make you a living; self-education will make you a fortune. -- Jim Rohn
You have enemies? Good. That means you&#8217;ve stood up for something, sometime in your life. -- Winston Churchill
The best thing about the future is that it comes only one day at a time. -- Abraham Lincoln
The friendship that can cease has never been real. -- Saint Jerome
Once you forget what you&#8217;re worth, you forget what you deserve. -- Unknown
It&#8217;s not how much we give but how much love we put into giving. -- Mother Teresa
Excellence is not a skill. It is an attitude. -- Ralph Marston
Don&#8217;t be afraid of being unique. It&#8217;s like being afraid of your best self. -- Donald Trump
In prosperity our friends know us; in adversity we know our friends. -- John Churton
You&#8217;ll never find a rainbow if you&#8217;re looking down. -- Charlie Chaplin
No matter what you do or say, there&#8217;s nothing you can do to make people understand you. -- Kurt Cobain
There has to be evil so that good can prove its purity above it. -- Buddha
We would accomplish many more things if we did not think of them as impossible. -- Vince Lombardi
If you&#8217;re not making mistakes, you&#8217;re not doing anything. -- Susan Sarandon
All progress occurs because people dare to be different. -- Harry Millner
Continuous improvement is better than delayed perfection. -- Mark Twain
You cannot do a kindness too soon, for you never know how soon it will be too late. -- Ralph Waldo Emerson
If you knew how much work went into it, you wouldn&#8217;t call it genius. -- Michelangelo
Reading is to the mind what exercise is to the body. -- Sir Richard Steele
Inside every older person is a younger person &#8211; wondering what the hell happened. -- Unknown
A good laugh and a long sleep are the best cures in the doctor&#8217;s book. -- Irish Proverb
Obstacles are those frightful things you see when you take your eyes off your goal. -- Henry Ford
Whatever is begun in anger ends in shame. -- Benjamin Franklin
People who say it cannot be done should not interrupt those who are doing it. -- George Bernard Shaw
Anger is only one letter short of danger. -- Unknown
Everyone thinks of changing the World, but no one thinks of changing himself. -- Leo Tolstoy
Nobody is worth your tears, and the one who is, won&#8217;t make you cry. -- Unknown
Deal with the world the way it is, not the way you wish it was. -- John Chambers
An eye for an eye only makes the whole world blind. -- Gandhi
Don&#8217;t make decisions when you&#8217;re angry. Don&#8217;t make promises when you&#8217;re happy. -- Unknown
Every child is an artist. The problem is how to remain an artist once we grow up. -- Pablo Picasso
If you don&#8217;t pursue what you think will be most meaningful, you will regret it. Life is long. There is always time for Plan B. But don&#8217;t begin with it. -- Drew Faust
A man is not old until regrets take the place of dreams. -- John Barrymore
Change is the law of life. And those who look only to the past or present are certain to miss the future. -- John F. Kennedy
You really shouldn&#8217;t say &#8216;I love you&#8217; unless you mean it. But if you mean it, you should say it a lot. People forget. -- Unknown
We are all in the gutter, but some of us are looking at the stars. -- Oscar Wilde
Each new effort brings you closer to the one that might really work. -- Bob Greene
Dream as if you&#8217;ll live forever. Live as if you&#8217;ll die today. -- James Dean
He who receives an idea from me, receives instruction himself without lessening mine; as he who lights his taper at mine, receives light without darkening me. -- Thomas Jefferson
My fault, my failure, is not in the passions I have, but in my lack of control of them. -- Jack Kerouac
For every minute you are angry you lose sixty seconds of happiness. -- Ralph Waldo Emerson
Pleasure in the job puts perfection in the work. -- Aristotle
The distance between insanity and genius is measured only by success. -- Bruce Feirstein
What we do for ourselves dies with us. What we do for others and the world, remains and is immortal. -- Albert Pine
There is no limit to the good one can do, when he cares not who gets the credit. -- Unknown
We are here to add what we can to life, not to get what we can from life -- William Osler
Laziness grows on people; it begins in cobwebs and ends in iron chains. -- Samuel Taylor Coleridge
When the power of love overcomes the love over power, the world will know peace. -- Jimi Hendrix
Be kind, for everyone you meet is fighting a hard battle. -- Pluto
People who drink to drown their sorrow should be told that sorrow knows how to swim. -- Ann Landers
The truth will set you free &#8211; but first it will make you miserable. -- Unknown
&#8220;Fire tests gold, misery tests strong men. -- Seneca
```

You can see the results in the screenshots. This is the way I could think of of doing this. xD If you know a better way, I'd like to hear about it. Thanks!

---

### Post by dv3500ea on 2010-08-05
You could do something similar with SVG wallpapers and a bit of programming.
Someone made a script to show twitter posts on their wallpaper:
[http://buzypi.in/2010/05/22/the-power-of-ubuntu-showing-dynamic-messages-in-your-desktop-background/]("http://buzypi.in/2010/05/22/the-power-of-ubuntu-showing-dynamic-messages-in-your-desktop-background/")
A method like this means you can have an image instead of a plain black background and that you don't need conky.

---

### Post by jpmelos on 2010-08-05
Wow, that's quite interesting! I think it's even better than my way, probably. Thanks, I'll try to use it. :D

---

