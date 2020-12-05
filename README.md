
# Crypt
![Build](https://github.com/DavW/crypt/workflows/Build/badge.svg)

**Crypt** is a software synthesiser plugin designed for creating spacious cold hyper-unisoned
synth sounds; developed by [Vitling](https://www.vitling.xyz) for the [Bow Church](http://bowchurch.bandcamp.com/) project.

![Screenshot](https://github.com/DavW/crypt/blob/main/screenshot.jpg?raw=true)

It is written in C++17 and depends on the [JUCE](https://github.com/juce-framework/JUCE) framework, which is
included as a submodule.

## Installation

### Mac

On versions of macOS pre-Catalina, you can simply grab the latest build from the [Release Page](https://github.com/DavW/crypt/releases)
and copy it into your `/Library/Audio/Plug-Ins/VST3` or `~/Library/Audio/Plug-Ins/VST3` folder.

Starting with macOS 10.15 Catalina, Apple have taken a sinister anti-competitive, anti-open-source and anti-indie-developer step to prevent
developers from releasing software without also paying to join Apple's Developer Program. This means that it is impossible
for me to provide a standard installer to you without paying Apple money. This is done under the guise of the anti-malware "notarization"
process but with no access to the notarization process without paying, even for open source developers, they're effectively
putting up a paywall to developing for macOS.

#### Workaround 1

As of version 10.15, there is a workaround, and that's to use cURL in the Terminal to download the software, which doesn't
set that quarantine bit that is checked by the Gatekeeper software inside macOS. Therefore, you can install the plugin for macOS by copying and
pasting the following line into the Terminal application and pressing enter.

```sh
curl -L https://github.com/DavW/crypt/releases/download/v0.3.0/crypt-mac-vst3.tar.gz --output crypt-mac-vst3.tar.gz && tar -zxvf crypt-mac-vst3.tar.gz && mkdir -p ~/Library/Audio/Plug-Ins/VST3/ && mv Crypt.vst3 ~/Library/Audio/Plug-Ins/VST3/ && echo "Crypt VST3 plugin installed successfully"
```
You should ***NEVER*** run random code snippets like this from the internet without understanding what they are doing, so for information purposes let me also break it down for you:

First it downloads the plugin from GitHub and saves it:
`curl -L https://github.com/DavW/crypt/releases/download/vx.x.x/crypt-macos-x.x.x.tar.gz --output crypt-mac-vst3.tar.gz`
Next it extracts the VST3 plugin onto your hard disk: `tar -zxvf crypt-mac-vst3.tar.gz`
Then we make sure that you have a VST3 plugin folder on your system with `mkdir -p ~/Library/Audio/Plug-Ins/VST3/`
Finally we move the VST3 version of the plugin into your plugins folder
`mv Crypt.vst3 ~/Library/Audio/Plug-Ins/VST3/`

If you think that Open Source, Freeware and Indie developers shouldn't have to do this, and not pay Apple for the "privilege" of making software
for their (already massively expensive and profitable) hardware, then I suggest you contact Apple to complain, and contact your elected representatives
to push for legislation outlawing this kind of behaviour. Not only does it have cost implications for developers, but it also gives Apple the final
say on what software is and isn't allowed to run on the computers they produce, paving the way for censorship and power consolidation on their part.

#### Workaround 2

The alternative to the above, is to download the binary as normal, then unset the quarantine bit on the archive you've just downloaded, then copy it into
your plugin folder yourself. You can do this with the `xattr` command

```bash
xattr -d com.apple.quarantine crypt-mac-vst3.tar.gz
```

After doing this you should be able to extract the archive and copy the plugin into your plugins folder and have it work without any problems

### Windows

Windows builds are also built by the GitHub Actions CD system, but I do not have a Windows computer available to verify that they work
as expected. If you're a Windows user, please let me know how your experience is and whether it works or not.

You can download whatever binaries that JUCE produces during the make process from the [Release Page](https://github.com/DavW/crypt/releases) and copy them into your VST3 plugin folder


### Linux

Building on Linux should be fairly straightforward, but I had some slightly confusing linker errors when I tried. Let me know if you manage to get it to work.

#### Dependencies
```cmake g++ libfreetype6-dev libx11-dev libxinerama-dev libxrandr-dev libxcursor-dev mesa-common-dev libasound2-dev freeglut3-dev libxcomposite-dev pkg-config```

These are Debian/Ubuntu package names (install with `sudo apt-get install ` and paste the above), you may need to translate for your distro

#### Build

```bash
git clone --recursive --shallow-submodules https://github.com/DavW/crypt.git
cmake -S crypt -B crypt-build
cmake --build crypt-build --config Release --verbose
```

## Support

If you find this useful, then please consider supporting my work. You can do that by buying the music of [Bow Church](https://bowchurch.bandcamp.com)
or [Vitling](https://vitling.bandcamp.com); or listen and add to playlists on Spotify and/or SoundCloud.

You can also see my [website](https://www.vitling.xyz), [Instagram](https://instagram.com/vvitling) or [Twitter](https://twitter.com/vvitling) to follow
my latest work; and/or contact me to hire me for stuff.

## License

This plugin is free software, licensed under the [GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html). 

However, the JUCE framework that it depends on as a submodule has [its own license](https://github.com/juce-framework/JUCE/blob/master/LICENSE.md)