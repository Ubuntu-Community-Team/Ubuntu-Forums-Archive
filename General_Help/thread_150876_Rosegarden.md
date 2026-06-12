---
title: "Rosegarden"
date: 2006-03-26
forum: General Help
---

### Post by Micro$oftWinblows on 2006-03-26
Forgive me if there's already a thread regarding Rosegarden, and if this thread isn't in the right place.

I searched about and found that Rosegarden has problems with Ubuntu, or vice versa, but I couldn't find anyone with the same problem that I have.

I'm a noob so if anyone could make sense of the following and resolve it, it'd be much appreciated.

To begin with, I'm prompted with the a screen saying:

"The Rosegarden sequencer could not be started, so sound and recording will be unavailable for this session.
For assistance with correct audio and MIDI configuration, go to http://rosegardenmusic.com"

And yes, I went there but it wasn't any help.

This is what's said in the console...

lw@Ubuntu:~$ rosegarden4
kbuildsycoca running...
rosegarden: main: Showing startup logo
lw@Ubuntu:~$ rosegarden (sequence manager): getSequencerPlugins - getting plugin information
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
[/home/lw/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa]
rosegarden (sequence manager): got 63629 pieces of plugin data at GUI side
Profiler : id = querying plugins - elapsed = 730ms CPU,  1.246982000R real
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden (sequencer): SequencerMmapper : setting size of /tmp/kde-lw//rosegarden_sequencer_timing_block to 91012
rosegarden (sequencer): SequencerMmapper : mmap size : 91012 at 0xb61a0000
rosegarden (sequencer): SequencerMmapper::init()
rosegarden (sequencer): Registering with DCOP server
Rosegarden 1.0 - AlsaDriver - alsa-lib version 1.0.9

JackDriver::initialiseAudio - JACK server not running
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up

... It says the last line a few tens more

rosegarden: couldn't kill any sequencer processes
rosegarden: RosegardenGUIApp::slotSequencerExited Sequencer exited
rosegarden: RosegardenGUIApp::slotSequencerExited Sequencer exited
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00285
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a00285
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x2a00285
rosegarden: RosegardenGUIApp::queryExit
Profiler : id = RosegardenGUIDoc::syncDevices - elapsed = 140ms CPU,  62.882467000R real
rosegarden: RosegardenGUIDoc::openDocument(/usr/share/apps/rosegarden4/autoload.rg)
rosegarden: RosegardenGUIDoc[0x8b78918]::setModified(false)
rosegarden: RosegardenProgressDialog::RosegardenProgressDialog type 2 - Reading file... - modal : true
rosegarden: "zoomlevel" value = 38399
rosegarden (sequence manager): RoseXmlHandler::skipToNextPlayDevice; m_deviceRunningId is 10000
rosegarden (sequence manager): RoseXmlHandler::skipToNextPlayDevice: fresh out of devices
rosegarden (sequence manager): RoseXmlHandler::addMIDIDevice - can't call sequencer addDevice
RosegardenGUIDoc::xmlParse (reader.parse()): 30ms elapsed
rosegarden: RosegardenGUIDoc::openDocument() end - m_composition : 0x8b7898c - m_composition->getNbSegments() : 0 - m_composition->getDuration() : 0
rosegarden: RosegardenGUIDoc[0x8b78918]::setModified(false)
rosegarden: MultiViewCommandHistory::attachView() : setting up undo/redo actions
rosegarden: RosegardenGUIApp::initView()
rosegarden: TrackEditor::slotReadjustCanvasSize() : width = 10100, nbTracks = 64
rosegarden: TrackEditor::slotReadjustCanvasSize - done
rosegarden: TrackEditor::setupSegments() begin
Profiler : id = StudioControl::sendQuarterNoteLength - elapsed = 0ms CPU,  0.000456000R real
rosegarden: TrackEditor::scrollToTrack(0) scrolling to Y 0
rosegarden: useInstrument() - populate Instrument
rosegarden: SegmentSelector()
rosegarden: SegmentSelector::clearSelected()
rosegarden: RosegardenGUIApp::slotStateChanged have_selection,true
rosegarden: RosegardenGUIApp::slotStateChanged audio_segment_selected,true
rosegarden: SegmentCanvas::slotSetTool(segmentmover)[SegmentCanvas pointer (0x8bc0300) to unnamed widget, geometry=100x30+0+0]
rosegarden: SegmentMover()
rosegarden: SegmentCanvas::slotSetTool(segmentpencil)[SegmentCanvas pointer (0x8bc0300) to unnamed widget, geometry=100x30+0+0]
rosegarden: SegmentPencil()
rosegarden: RosegardenGUIApp::slotChangeZoom : zoom size = 38.4
rosegarden: RosegardenGUIView::setZoomSize - xScale =  1
rosegarden: SegmentCanvas::updateSegmentItemSelection
rosegarden: SegmentSelector::clearSelected()
rosegarden (notation): Returning chord-label ruler width as 10100
rosegarden (notation): Returning chord-label ruler width as 10100
rosegarden (notation): Returning chord-label ruler width as 10100
rosegarden (notation): Returning chord-label ruler width as 10100
Profiler : id = RosegardenGUIDoc::syncDevices - elapsed = 0ms CPU,  0.000009000R real
rosegarden: RosegardenGUIDoc[0x8b78918]::setModified(false)
rosegarden: RosegardenGUIApp::slotDocumentModified(false) - doc path =
rosegarden: RosegardenGUIApp::slotStateChanged new_file_modified,false
rosegarden: RosegardenGUIDoc[0x8b78918]::setModified(false)
rosegarden: RosegardenGUIApp::slotDocumentModified(false) - doc path =
rosegarden: RosegardenGUIApp::slotStateChanged new_file_modified,false
rosegarden: TrackEditor::slotReadjustCanvasSize() : width = 10100, nbTracks = 64
rosegarden: TrackEditor::slotReadjustCanvasSize - done
rosegarden (sequence manager): CompositionMmapper() - doc = 0x8b78918
rosegarden (sequence manager): ControlBlockMmapper : setting size of /tmp/kde-lw//rosegarden_control_block to 8220
rosegarden (sequence manager): ControlBlockMmapper : mmap size : 8220 at 0xb6459000
rosegarden (sequence manager): ControlBlockMmapper::initControlBlock()
rosegarden (sequence manager): SegmentMmapper : 0x8c54e00 trying to mmap /tmp/kde-lw//rosegarden_metronome
rosegarden (sequence manager): SegmentMmapper : mmap size = 0
rosegarden (sequence manager): MetronomeMmapper ctor : 0x8c54e00
rosegarden (sequence manager): MetronomeMmapper: no metronome for device 0
rosegarden (sequence manager): SegmentMmapper::setFileSize() : setting size of /tmp/kde-lw//rosegarden_metronome to 38404 - current size = 38404
rosegarden (sequence manager): SegmentMmapper::doMmap() - mmap size : 38404 at 0xb62c7000
rosegarden (sequence manager): MetronomeMmapper::dump: instrument is 0
rosegarden (sequence manager): MetronomeMmapper::dump: - Total events written = 480
rosegarden (sequence manager): SegmentMmapper : 0x8c0b400 trying to mmap /tmp/kde-lw//rosegarden_tempo
rosegarden (sequence manager): SegmentMmapper : mmap size = 0
rosegarden (sequence manager): SegmentMmapper::setFileSize() : setting size of /tmp/kde-lw//rosegarden_tempo to 4 - current size = 4
rosegarden (sequence manager): SegmentMmapper::doMmap() - mmap size : 4 at 0xb62c6000
rosegarden (sequence manager): SegmentMmapper : 0x8bff948 trying to mmap /tmp/kde-lw//rosegarden_timesig
rosegarden (sequence manager): SegmentMmapper : mmap size = 0
rosegarden (sequence manager): SegmentMmapper::setFileSize() : setting size of /tmp/kde-lw//rosegarden_timesig to 4 - current size = 4
rosegarden (sequence manager): SegmentMmapper::doMmap() - mmap size : 4 at 0xb62c5000
rosegarden: SequencerMapper::SequencerMapper - mmapping /tmp/kde-lw//rosegarden_sequencer_timing_block
rosegarden: SequencerMapper::map() : 0xb62ae000,91012
rosegarden: RosegardenGUIApp::slotStateChanged got_audio,false
Profiler : id = StudioControl::sendMappedComposition - elapsed = 0ms CPU,  0.000362000R real
Profiler : id = StudioControl::sendMappedEvent - elapsed = 10ms CPU,  0.004087000R real
rosegarden: RosegardenGUIDoc::initialiseStudio - clearing down and initialising
rosegarden: cleared studio
rosegarden (sequence manager): createStudioObject - failed to contact Rosegarden sequencer
Profiler : id = StudioControl::createStudioObject - elapsed = 0ms CPU,  0.046227000R real
Profiler : id = StudioControl::setStudioObjectProperty(float) - elapsed = 0ms CPU,  0.000396000R real
rosegarden (sequence manager): createStudioObject - failed to contact Rosegarden sequencer
Profiler : id = StudioControl::createStudioObject - elapsed = 0ms CPU,  0.000350000R real
Profiler : id = StudioControl::setStudioObjectProperty(float) - elapsed = 0ms CPU,  0.000121000R real
rosegarden (sequence manager): createStudioObject - failed to contact Rosegarden sequencer
Profiler : id = StudioControl::createStudioObject - elapsed = 0ms CPU,  0.021161000R real
Profiler : id = StudioControl::setStudioObjectProperty(float) - elapsed = 0ms CPU,  0.000082000R real
Profiler : id = StudioControl::setStudioObjectProperties(floats) - elapsed = 0ms CPU,  0.000068000R real
Profiler : id = StudioControl::sendMappedComposition - elapsed = 0ms CPU,  0.000049000R real
Profiler : id = StudioControl::sendMappedEvent - elapsed = 0ms CPU,  0.000111000R real
Profiler : id = initialiseStudio - elapsed = 0ms CPU,  0.070013000R real
Profiler : id = StudioControl::sendMappedComposition - elapsed = 0ms CPU,  0.000044000R real
Profiler : id = StudioControl::sendMappedEvent - elapsed = 0ms CPU,  0.000098000R real
Profiler : id = StudioControl::sendMappedComposition - elapsed = 0ms CPU,  0.000058000R real
Profiler : id = StudioControl::sendMappedEvent - elapsed = 0ms CPU,  0.000112000R real
Profiler : id = StudioControl::sendMappedComposition - elapsed = 0ms CPU,  0.000043000R real
Profiler : id = StudioControl::sendMappedEvent - elapsed = 0ms CPU,  0.000096000R real
rosegarden: RosegardenGUIApp::setupFileDialogSpeedbar
rosegarden: RosegardenGUIApp::setupFileDialogSpeedbar: examples set true
rosegarden: RosegardenGUIApp::showEvent()
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: TrackEditor::paintEvent: composition is modified, update everything
rosegarden: TrackEditor::slotReadjustCanvasSize() : width = 10100, nbTracks = 64
rosegarden: TrackEditor::slotReadjustCanvasSize - done
rosegarden: RosegardenGUIApp::slotStateChanged have_segments,false
rosegarden: RosegardenGUIApp::slotStateChanged have_selection,false
rosegarden (sequencer): SequencerMmapper : setting size of /tmp/kde-lw//rosegarden_sequencer_timing_block to 91012
rosegarden (sequencer): SequencerMmapper : mmap size : 91012 at 0xb620a000
rosegarden (sequencer): SequencerMmapper::init()
rosegarden (sequencer): Registering with DCOP server
Rosegarden 1.0 - AlsaDriver - alsa-lib version 1.0.9

JackDriver::initialiseAudio - JACK server not running
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
rosegarden: RosegardenGUIDoc::getCurrentTimer - failed to contact Rosegarden sequencer
rosegarden: RosegardenGUIDoc::setCurrentTimer - failed to contact Rosegarden sequencer
rosegarden: RosegardenGUIDoc::syncDevices - got unknown returntype from getDevices()
Profiler : id = RosegardenGUIDoc::syncDevices - elapsed = 240ms CPU,  2.221073000R real
rosegarden: sfxload disabled
rosegarden: RosegardenGUIApp::slotSequencerExited Sequencer exited


I did the following, thinking Jack might be the problem: sudo apt-get install jackd jackeq jack-rack jamin qjackctl


I've no idea. :neutral: 

Cheers.

---

### Post by Micro$oftWinblows on 2006-03-26
Blah, sorry about the emoticons in the post... I don't know what I'm doing.

---

### Post by Aphorism on 2006-03-26
My friend had the same issue.

The problem was that the sequencer modules were not loaded.

Also, you will need to boot jack up to get everything up and working.

A) Load your sequencer modules for your given soundcard.
B) Load jackd.

Good luck.

---

### Post by Micro$oftWinblows on 2006-03-26
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=C-Media&card=CMI8738&chip=CMI8738&module=cmipci#modp](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=C-Media&card=CMI8738&chip=CMI8738&module=cmipci#modp)

I found this, but, being a noob, I've no idea what I'm doing. Why isn't there an easy sudo-apt get install function for everything :(

---

### Post by Micro$oftWinblows on 2006-03-26
Would Rosegarden work (better) with Kubuntu?

---

### Post by stmiller on 2006-03-27
Rosegarden doesn't require jack. But many softsynths DO require jack. (So it is strongly recommended.) But you shouldn't be getting these errors.

Make sure you have these modules loaded:

snd-pcm-oss
snd-seq

If not, try sudo modprobe snd-pcm-oss
and then sudo modprobe snd-seq

to load them. Put them in your /etc/modules to have them load at boot.

---

### Post by Micro$oftWinblows on 2006-03-28
sudo modprobe snd-pcm-oss
sudo modprobe snd-seq

This got it working. 

Cheers.

---

### Post by koryo88 on 2006-11-14
Sorry to resurrect an old thread, but I had this same problem and it fixed it. How do I put those in the etc/modules folder to have them load at boot like he suggested?

---

### Post by Steve White on 2006-12-24
First, 
```
modprobe snd_seq 
```
does allow Rosegarden to start.

I added a line
```
snd_seq
```
to my /etc/modules file as well

But I get no sound when I play a MIDI file.  However, other sound programs work well.

There was some talk about installing "jack".  I did this, to no effect.

---

### Post by peter3 on 2008-03-14
Rosegarden seems to want an low latency kernel.
I do not find such a package in gutsy (7.10).
Previously (in Debian and other distros) I built my own kernel and included low latency
parameters.  But one of the motivations for moving to Ubuntu was so things would
"just work".  
Does Ubuntu have a solution to the low latency requirement in Rosegarden yet?

Thank you.

---

### Post by zukakog on 2008-03-24
> **peter3 said:**
> Rosegarden seems to want an low latency kernel.
I do not find such a package in gutsy (7.10).
Previously (in Debian and other distros) I built my own kernel and included low latency
parameters.  But one of the motivations for moving to Ubuntu was so things would
"just work".  
Does Ubuntu have a solution to the low latency requirement in Rosegarden yet?

Thank you.
Try [Ubuntu Studio]("http://ubuntustudio.org/"). It includes a realtime kernel. A fresh install is always a good idea, but you might have luck just doing
```
sudo aptitude install ubuntustudio-desktop
```

---

### Post by the_darkside_986 on 2008-05-01
So I would have to install a distro meta-package just to get sound to come out of rosegarden? I'm importing some sound fonts like I do in OpenMPT, but nothing seems to work. I don't really like MIDI's anyway; mikmod is better. Why can't someone port OpenMPT to GTK+Unix? (well, besides the awful mess of trying to use and learn GTK libraries.)

---

