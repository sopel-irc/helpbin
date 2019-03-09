# helpel

Help service for Sopel. Like a pastebin, but accepts only a strict data format
so as to limit abuse potential. Intended as a hedge against pastebins like
ptpb.pw shutting down, when Sopel uses pastebins for help output.

Also self-hostable for Sopel users with high-demand instances.

## Planned Features

* Cache help information for Sopel instances (if enabled; Sopel will have this
  off by default, for privacy considerations)
  * Updated by Sopel on start and module events (load, reload, unload)
  * Stores a custom data format, not raw text, so the service is not useful to
    would-be abusers for storing and distributing arbitrary data
* Display formatted command information via link
  * Submitted help data is transformed to static HTML, so server load should be
    minimal—no need for a heavy app server
* Expire cached data after some reasonable amount of time
  * helpel-enabled Sopel instances must ping the service periodically with a
    token value, or it will delete their data eventually
  * The same Sopel instance submitting updated help data should overwrite any
    old entries that exist for that instance (but securely, without collisions)

## Inspiration

Thanks to @half-duplex for the idea. Work on this will probably begin after
Sopel 7 is ready to go, because there's already a lot planned for that release.
Hopefully the world won't lose too many more pastebins before then.
