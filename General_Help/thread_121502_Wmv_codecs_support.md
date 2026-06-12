---
title: "Wmv codecs support"
date: 2006-01-25
forum: General Help
---

### Post by mjunior on 2006-01-25
Hello guys,

I'm running Ubuntu Brezy in Gnome version for a few months and almost convinced that is already possible to shift completly from WinXP to linux. Despite  the Open Office still didn't suite all my needs and also isn't fully compatible with Microsoft Office (which means at the office I'll still need to be a Bill's slave), the other features impressed me so far.
Recently I try to run multimedia files (video and audio)...I realize that most of the formats such as mp3,wma,wmv,avi,mpeg,etc..isn't supported by default..
Following the Ubuntu forums I was able to run some of the media files formats by installing new packages, but somehow the wmv ones are still a problem on my system.
The error message:The Totem could not play'File.wmv'.This file is encrypted and cannot be played back.

Already tried the toten xine,vlc,w32codecs,xine ui,mplayer,realplayer...and also tried to run the automatix script filling all the audio/video correlated options.
Searching for ~/.gnome2/totem_config... I cluld find the toten is pointing to the right w32 location...(usr/lib/win32):
# path to RealPlayer codecs
# string, default:
decoder.external.real_codecs_path:/usr/lib/win32

# path to Win32 codecs
# string, default: /usr/lib/win32
decoder.external.win32_codecs_path:/usr/lib/win32



No clue what I'm missing...any help is welcomed!

---

### Post by njzillest on 2006-01-25
use automatix it can be found on google or on the forums. It installs the codecs for Xine, totem player, and M player. It also downloads and installs many other apps, that you can choose from a list such as lime wire and bit torrent. You wil be able to play most files such as AVI, and MPG. Automatix also installs the plugins for Mozilla firefox (very usefull.)


i hope this helps

---

### Post by GTvulse on 2006-01-25
[quote="mjunior"]The error message:The Totem could not play'File.wmv'.This file is encrypted and cannot be played back.[/quote]

I wouldn't even bother. Using DRM wmv files is a very common form of Trojan Horse used with Windows machines to infest them with malware and/or hijack them to be used in net-wide bot networks (that is, turn them into zombies for distributed spamming and network attacks.)  Every one wants to watch Britney dressed like Eve in Paradise, right?

Now, if you actually bought that content from a reputable source, you have discovered the evilness of DRM...  You can only play that video in the MS Windows installation you installed it and with the copy of Windows Media Player you used to activate it (and a couple other MS Windows installations if the license allows you to transfer the licenses at all). :-(

---

### Post by mjunior on 2006-01-25
Hello njzillest,
I forgot to mention so I edit my post right now...I already tried the Automatix (before my post) script by selecting almost all the options available there...
Hello dradul,
So you suggest give up from wmv for security reasons?? This is a advice or means is impossible to run it into the Ubuntu?

Thanks so far.

---

### Post by mustang on 2006-01-25
[QUOTE=mjunior]Hello njzillest,
I forgot to mention so I edit my post right now...I already tried the Automatix (before my post) script by selecting almost all the options available there...
Hello dradul,
So you suggest give up from wmv for secutity reasons?? This is a advice or means is impossible to run it into the Ubuntu?

Thanks so far.[/QUOTE]

Hi mrjunior,

assuming you have access to a windows system, does that file play fine on it? Or does it also give you problems in windows as well? I'm pretty sure it's not a codec problem if you have installed them (but you could always check by googling for a sample wmv file and see if it works or not)

Perhaps you can look around for a method that strips the drm from the wmv??

---

### Post by mjunior on 2006-01-25
Hello Mustang,
The answer is yes. I have another partition with WinXP on it, so I can test the wmv files by booting again...The files I wanna see can be loaded normaly by Windows Media Player.

Forgive my dumb question, but when you mentioned drm..did you mean some signature, or something? Could you guide me some related issue on linux?

---

### Post by Lem on 2006-01-25
You need w32codecs. You can get them from the marrilat sources amongst other places.

---

### Post by GTvulse on 2006-01-25
That would be me who mentioned DRM (Digital Rights Management). That's a very complex issue you really need to research on your own; I would summarize it as stealing your right of fair copy and access to information[1] by international media corporations by restricting your acess to information through the use of military grade encryption which in the future will be based on hardware platforms such as the new Intel offerings to be used with MS Windows Vista. Usually applies to trivial stuff such as the latest Britney Spears pr0n video or the latest MTV hits, but soon it could cover the works of Eça de Queiroz[2] or even Shakespeare, even if by law they are in the public domain. (That's where most of Bill Gates personal investments have been in the last ten years btw, acquiring the rights on all internet viewing of the Monalisa to give you an example.)  How would you feel if you had to pay an overseas company to listen to the music of a national icon such as Vinicius De Moraes?

Anyway, this is something more proper to the Community Chat forums, let's move it there.

[1] Don't believe that you don't be affected, that's one of the reason's why your president is so adamant on open source software, and the guy north of your country is trying to implement (and we west of your country should be, but are not because of reasons I know too well... Remember, I'm 2600 m of paranoia above sea level in the middle of the Neotropic, you are just above sea level and a little South of the Equator... ;-)).

[2] My favorite XIX Century novelist :-)

---

### Post by leonbrio on 2006-05-20
well, i had some issue from DRM files before.
therefore there are converters on windows (search it) that strips drm out[1].
even apple nowadays is throwing drm away (yes, they are starting to sell non drm on itunes. because of the various issues that these files cause at all)


can't really help ya coz i'm just in my first day on using linux (maybe i regret of installing AMD64 pack version)

anyway, gts someone from the same country here =)

i'm not fully convinced of throwing away win, coz of games, win can't read ext3, linx can't deal with nfts, and fat32 runs just too slow on win for me.

too bad that i can't download more mp3 at linx coz i won't be able to listen then on win. =/

[1] assuming also that this is the only thing that stops you from watching on linux.

---

### Post by mjunior on 2006-05-20
The DRM issue is a completly black cloud for me..till now. Althogh I understood this is a matter of author rights reserved guarantee or so...which on videos, have the same sympthom as encripted files...
I would try your tip stripping drm off my files, but fortunally I don't use Windows anymore...
 As for your regrets on installing Linux..I felt kind of the same way at the very first week or so. My worries tough, was mainly regarding the Ms Office compliance... which I'm far at ease since starts to realize the OpenOffice potential.

As for your concern about ext3 and NTFS accessibility, I really think is in vain. And you surely will have no issue to access NTFS partitions from linux. As for the windows, the ext3 is absolutely out or reach..so what you could do (this is how I managed this matter on my pc while I had windows and linux together) is split your HD, saving a NTFS or Fat partitions where you can store your media files...that way you can achieve them regardles the os you boot up.

Try this link for further about NFTS accessibility...
[http://breezy.ubuntuguidebrasil.org/#automountntfs](http://breezy.ubuntuguidebrasil.org/#automountntfs)

Ps. No site Ubuntu Brasil também tem boas dicas...você ja visitou?
[http://www.linuxval.org/ubuntu/phpBB2/](http://www.linuxval.org/ubuntu/phpBB2/)

---

### Post by leonbrio on 2006-05-20
as far as i'm concerned linux does never writes on ntfs, it just reads from it. that's my big problem. i can listen to my mp3 on linux, but i can only organize them in windows.

my problem now, is coz i usually keep media files on one hd, and the oses and program in other.(as i'm allways listening to mp3...)

and i do play few games that doesn't run on linux (one of them, beta testing, another one i pay monthly fee)
just not an option.

but i use gimp inkscape and openoffice on my win =0)

maybe u can find the programs for drm for lnx, if not, u can try Vmware or wine.

---

