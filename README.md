# AutoSkip for YouTube (Browser Extension) 

## Description

AutoSkip for YouTube is a Chrome extension designed to enhance the YouTube viewing experience by automatically skipping ads. I initially intended to use a script that clicked the "Skip ad" button when it appeared. It turns out that it is available in the source code from the start so it is possible to skip the ad without waiting. When it detects an ad but fails to find the skip button, this happens with the unskippable ads, it will mute and speed it up so it is almost unnoticeable. I guess this also counts as watching the full ad.

## Supported browsers

1. **Chromium**

All Chromium browsers (i.e. Chrome, Edge, Brave, Opera) will work the same way, see the installation below.

2. **Safari**

You have to build it from scratch or download the universal binary from [here](https://github.com/notarisj/YouTube-AutoSkip/releases/latest).

If you want to build it, you must have Xcode and sign it with your developer certificate or allow unsigned extensions every time you close it. Run the following command:

```bash
xcrun safari-web-extension-converter /path/to/YouTube-AutoSkip/src --macos-only --app-name "YouTube AutoSkip"
```

If everything is correct you should see:

```bash
Xcode Project Location: /Users/<username>
App Name: YouTube AutoSkip
App Bundle Identifier: com.yourCompany.YouTube-AutoSkip
Platform: macOS
Language: Swift
```

After that, Xcode should open automatically. Build the app and copy it to  `Applications` folder. Open Safari, allow unsigned extensions (if not signed), and enable the extension from settings.

## Installation

1. Clone the repository or download the ZIP file.
2. Extract the files (if you downloaded a ZIP).
3. Open Google Chrome and navigate to chrome://extensions/.
4. Enable 'Developer Mode'.
5. Click on 'Load Unpacked' and select the `src` folder.
6. Enjoy ad-free YouTube viewing!

## How it Works

The extension uses a content script with a MutationObserver to dynamically observe elements such as the "Skip ad" button, as well as various ad formats like banners. When it detects the "Skip ad" button it  automatically triggers it. When the button is not available, with unskippable ads, it will verify that `ytp-ad-player-overlay` exists, mute the audio and set the playback rate to 10x.

## Limitations

* ~~Unskippable Ads: The extension cannot skip ads that do not have the "Skip Ad" option.~~
* YouTube Updates: Changes in YouTube's front-end design or ad mechanisms may affect the extension's functionality.

## Disclaimer

This project is created for educational purposes and personal use. The author has no responsibility for any disruptions or violations of YouTube's terms of service. Users should employ this extension at their own risk and discretion.

## License
This project is open-source and available under the [MIT License](LICENSE).
