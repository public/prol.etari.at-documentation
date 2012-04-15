# prol.etari.at

I have a VPS. It runs Debian stable. I use it for a lot of things. This documentation is as much about what the point of having my own VPS is as much as it is about the software I use to implement it.

Ultimately I'm planning to get all of this madness turned into a fabric/chef/puppet script.

## SSL

I have an actual CA signed SSL cert from namecheap.com which most of my services use. The convenience of not fighting with self-signed certs clients with dodgy SSL implementations is totally worth the ~£6/year.

## E-mail

I host my own e-mail. I used to use Gmail but Gmail has an awful IMAP implementation and these days search is weirdly slow.

### exim4

Pretty much the standard Debian single file exim configuration. I've enabled DKIM and SpamAssasin and have a valid SPF record in DNS. Getting the config for this to actually work was a bit of a pain because debugging exim is a bit of a black art.

### Dovecot

I recently switched from Cyrus to Dovecot. It's a lot faster for my use.

The configuration is pretty much exactly what you get from the Debian package but with plaintext IMAP disabled entirely.

## Instant Messaging

Prosdy. ejabberd is way too complicated for this use-case.

## IRC

irssi in GNU screen.

## Home Theatre Tunnel

I have a home server. I don't particularly want to expose it directly to the internet because I have limited upstream bandwidth and it's generally a bit slow. So I use vtund, iptables and a Varnish cache to control and limit it's exposure to the interwebs.

### Media streaming

Obviously there's lots of awesome music and videos on this thing. If I'm going to hoard them all I might as well make them easy to use too. 

I run a varnish instance that proxies several HTTP services from the HTPC to the internet. Media streaming is done through Subsonic. This gives me real-time transcoding and streaming of video to my browser or mobile phone from my home. It's like having a private NetFlix and Spotify server rolled into one. Sadly it doesn't support HTML5 video/audio yet so I have to endure Flash :(
