# SwiftyAcknowledgements

SwiftyAcknowledgements makes it easy to integrate acknowledgements for third party libraries into your iOS Apps.

## Requirements

- iOS 9.0 or higher
- Xcode 7.0 or higher

## Components

SwiftyAcknowledgements consists of two components.

### Script

`GenerateLicenseFile.swift` is a Swift script that scans a directory for files named `LICENSE` or `LICENSE.txt` and generates a property list containing the content of every license along with a name. The name will be set to the name of the folder that the corresponding license file is contained in.

### Framework

**SwiftyAcknowledgements** comes with a framework `SwiftyAcknowledgements.framework` that can be used to visualize the generated license file within an iOS App. The framework contains a **TableViewController** and a **DetailViewController** and can be integrated programatically or using a **Storyboard**.

## Installation

### Carthage

[Carthage](https://github.com/Carthage/Carthage) is a decentralized dependency manager that builds your dependencies and provides you with binary frameworks.

To integrate **SwiftyAcknowledgements** into your Xcode projekct using **Carthage**, specify it in your `Cartfile`:

```
github "mathiasnagler/SwiftyAcknowledgements"
```

Follow the instructions in the [Carthage Documentation](https://github.com/Carthage/Carthage) to install the built framework into your Xcode project.

### Script

To integrate the script into your Xcode project create a subfolder `Scripts` in the folder that contains your Xcode project. Then, copy `GenerateLicenseFile.swift` to that subfolder. In your target, create a new `Run Script Build Phase` like this:

```
${SRCROOT}/Scripts/GenerateLicenseFile.swift ${SRCROOT}/Libraries/ ${PROJECT_DIR}/iOS\ Example/Acknowledgements.plist
```

**Note:** The first parameter for the script is the input directory that should be scanned for license files. The second parameter is the output file that should be generated by the script.

After that, build your project and add the generated license file to your Xcode project.

## Usage

The framework contains `AcknowledgementsTableViewController.swift` that can be pushed onto a `UINavigationController` or presented modally. The `AcknowledgementsTableViewController` will automatically for a file `Acknowledgements.plist` and display its contents. If your license file is named differently, you can specify your custom name using the property `acknowledgementsPlistName: String`.

## Credits

**SwiftyAcknowledgements** was inspired by Vincent Tourraine's [VTAcknowledgementsViewController](https://github.com/vtourraine/VTAcknowledgementsViewController).

## License

**SwiftyAcknowledgements** is available under the MIT license. See the LICENSE file for more info.
