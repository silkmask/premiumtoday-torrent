function RecentPostsScrollerv2(json) {
> var sHeadLines;
> var sPostURL;
> var objPost;
> var sMoqueeHTMLStart;
> var sMoqueeHTMLEnd;
> var sPoweredBy;
> var sHeadlineTerminator;
> var sPostLinkLocation;

> try {
> > sMoqueeHTMLStart = "\<MARQUEE behavior=\"scroll\" onmouseover=\"this.stop();\" onmouseout=\"this.start();\" ";


> if (nWidth) {
> > sMoqueeHTMLStart = sMoqueeHTMLStart + " width = \"" + nWidth + "%\"";

> } else {
> > sMoqueeHTMLStart = sMoqueeHTMLStart + " width = \"100%\"";

> }
> if (nScrollDelay) {
> > sMoqueeHTMLStart = sMoqueeHTMLStart + " scrolldelay = \"" + nScrollDelay + "\"";

> }
> if (sDirection) {
> > sMoqueeHTMLStart = sMoqueeHTMLStart + " direction = \"" + sDirection + "\"\>";


> if (sDirection == "left" || sDirection == "right") {
> > sHeadlineTerminator = "&nbsp;&nbsp;";

> } else {
> > sHeadlineTerminator = "\<br/\>";

> }
> }
> if (sOpenLinkLocation == "N") {
> > sPostLinkLocation = " target= \"_blank\" ";

> } else {
> > sPostLinkLocation = " ";

> }
> sMoqueeHTMLEnd = "\</MARQUEE\>"_

> sHeadLines = "";

> for (var nFeedCounter = 0; nFeedCounter < nMaxPosts; nFeedCounter++) {
> > var objPost = json.feed.entry[nFeedCounter](nFeedCounter.md);


> if (nFeedCounter == json.feed.entry.length) break;

> for (var nCounter = 0; nCounter < objPost.link.length; nCounter++) {
> > if (objPost.link[nCounter](nCounter.md).rel == 'alternate') {
> > > sPostURL = objPost.link[nCounter](nCounter.md).href;
> > > break;

> > }

> }
> sHeadLines = sHeadLines + "\<b\>" + sBulletChar + "\</b\> \<a " + sPostLinkLocation + " href=\"" + sPostURL + "\">" + objPost.title.$t + "\</a\>" + sHeadlineTerminator;
> }
> sPoweredBy = "<a href='\"http://www.justnaira.com/2012/08/auto-scrolling-recent-posts-widget-for-blogger-blogs.html\"\'>Grab This Widget\</a\> ~ \<a href='\"http://www.justnaira.com\"\'>Just Naira\</a\>";</li></ul>

> if (sDirection == "left") {
> > sHeadLines = sHeadLines + "&nbsp;&nbsp;" + sPoweredBy;

> } else if (sDirection == "right") {
> > sHeadLines = sPoweredBy + "&nbsp;&nbsp;" + sHeadLines;

> } else if (sDirection == "up") {
> > sHeadLines = sHeadLines + "\<br/\>" + sPoweredBy;

> } else {
> > sHeadLines = sPoweredBy + "\<br/\>" + sHeadLines;

> }
> document.write(sMoqueeHTMLStart + sHeadLines + sMoqueeHTMLEnd)
> } catch (exception) {
> > alert(exception);

> }
}