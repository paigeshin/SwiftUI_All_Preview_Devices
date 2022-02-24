# SwiftUI_All_Preview_Devices

```swift

enum AllDeviceNames: String, CaseIterable {
    case Mac = "Mac"
    case iPhone7 = "iPhone 7"
    case iPhone7Plus = "iPhone 7 Plus"
    case iPhone8 = "iPhone 8"
    case iPhone8Plus = "iPhone 8 Plus"
    case iPhoneSE = "iPhone SE"
    case iPhoneX = "iPhone X"
    case iPhoneXs = "iPhone Xs"
    case iPhoneXsMax = "iPhone Xs Max"
    case iPhoneXr = "iPhone Xʀ"
    case iPadMini4 = "iPad mini 4"
    case iPadAir2 = "iPad Air 2"
    case iPadPro_9_7 = "iPad Pro (9.7-inch)"
    case iPadPro_12_9 = "iPad Pro (12.9-inch)"
    case iPad_5Gen = "iPad (5th generation)"
    case iPadPro_12_9_2Gen = "iPad Pro (12.9-inch) (2nd generation)"
    case iPadPro_10_5 = "iPad Pro (10.5-inch)"
    case iPad_6Gen = "iPad (6th generation)"
    case iPadPro_11 = "iPad Pro (11-inch)"
    case iPadPro_12_9_3Gen = "iPad Pro (12.9-inch) (3rd generation)"
    case iPadMini_5Gen = "iPad mini (5th generation)"
    case iPadAir_3Gen = "iPad Air (3rd generation)"
    case AppleTV = "Apple TV"
    case AppleTV4K = "Apple TV 4K"
    case AppleTV4K_1080 = "Apple TV 4K (at 1080p)"
    case AppleWatch2_38 = "Apple Watch Series 2 - 38mm"
    case AppleWatch2_42 = "Apple Watch Series 2 - 42mm"
    case AppleWatch3_38 = "Apple Watch Series 3 - 38mm"
    case AppleWatch3_42 = "Apple Watch Series 3 - 42mm"
    case AppleWatch4_40 = "Apple Watch Series 4 - 40mm"
    case AppleWatch4_44 = "Apple Watch Series 4 - 44mm"
    
    static var all: [String] {
        return AllDeviceNames.allCases.map { $0.rawValue }
    }
}

// All Mac devices
enum MacDeviceNames: String, CaseIterable {
    case Mac = "Mac"
    
    static var all: [String] {
        return MacDeviceNames.allCases.map { $0.rawValue }
    }
}

// All iPhone devices
enum iPhoneDeviceNames: String, CaseIterable {
    case iPhone7 = "iPhone 7"
    case iPhone7Plus = "iPhone 7 Plus"
    case iPhone8 = "iPhone 8"
    case iPhone8Plus = "iPhone 8 Plus"
    case iPhoneSE = "iPhone SE"
    case iPhoneX = "iPhone X"
    case iPhoneXs = "iPhone Xs"
    case iPhoneXsMax = "iPhone Xs Max"
    case iPhoneXr = "iPhone Xʀ"
    
    static var all: [String] {
        return iPhoneDeviceNames.allCases.map { $0.rawValue }
    }
}

// All iPad devices
enum iPadDeviceNames: String, CaseIterable {
    case iPadMini4 = "iPad mini 4"
    case iPadAir2 = "iPad Air 2"
    case iPadPro_9_7 = "iPad Pro (9.7-inch)"
    case iPadPro_12_9 = "iPad Pro (12.9-inch)"
    case iPad_5Gen = "iPad (5th generation)"
    case iPadPro_12_9_2Gen = "iPad Pro (12.9-inch) (2nd generation)"
    case iPadPro_10_5 = "iPad Pro (10.5-inch)"
    case iPad_6Gen = "iPad (6th generation)"
    case iPadPro_11 = "iPad Pro (11-inch)"
    case iPadPro_12_9_3Gen = "iPad Pro (12.9-inch) (3rd generation)"
    case iPadMini_5Gen = "iPad mini (5th generation)"
    case iPadAir_3Gen = "iPad Air (3rd generation)"
    
    static var all: [String] {
        return iPadDeviceNames.allCases.map { $0.rawValue }
    }
}

// All Apple TV devices
enum AppleTVDeviceNames: String, CaseIterable {
    case AppleTV = "Apple TV"
    case AppleTV4K = "Apple TV 4K"
    case AppleTV4K_1080 = "Apple TV 4K (at 1080p)"
    
    static var all: [String] {
        return AppleTVDeviceNames.allCases.map { $0.rawValue }
    }
}

// All Apple Watch devices
enum AppleWatchDeviceNames: String, CaseIterable {
    case AppleWatch2_38 = "Apple Watch Series 2 - 38mm"
    case AppleWatch2_42 = "Apple Watch Series 2 - 42mm"
    case AppleWatch3_38 = "Apple Watch Series 3 - 38mm"
    case AppleWatch3_42 = "Apple Watch Series 3 - 42mm"
    case AppleWatch4_40 = "Apple Watch Series 4 - 40mm"
    case AppleWatch4_44 = "Apple Watch Series 4 - 44mm"
    
    static var all: [String] {
        return AppleWatchDeviceNames.allCases.map { $0.rawValue }
    }
}



```

# Sample Views

```swift

SampleView.swift
//
//  SampleView.swift
//  PickerTrivia
//
//  Created by RoLY roLLs on 12/30/19.
//  Copyright © 2019 RoLYroLLs Enterprises, LLC. All rights reserved.
//
import SwiftUI

struct SampleView: View {
    
    var body: some View {
        Text("Hello World!")
    }
}

// Show just 1 iPhone
struct SampleView_Previews_iPhoneXSMax: PreviewProvider {
    static var previews: some View {
        SampleView()
            .previewDevice(PreviewDevice(rawValue: AllDeviceNames.iPhoneXsMax.rawValue))
            .previewDisplayName(AllDeviceNames.iPhoneXsMax.rawValue)
    }
}

// Show 2 iPhones
struct SampleView_Previews_iPhoneXsMaxAndXs: PreviewProvider {
    static var previews: some View {
        ForEach([AllDeviceNames.iPhoneXs.rawValue, AllDeviceNames.iPhoneXsMax.rawValue], id: \.self) { devicesName in
            SampleView()
                .previewDevice(PreviewDevice(rawValue: devicesName))
                .previewDisplayName(devicesName)
        }
    }
}

// Show an iPhone and an iPad
struct SampleView_Previews_iPhoneXsMaxAndiPad: PreviewProvider {
    static var previews: some View {
        ForEach([AllDeviceNames.iPhoneXsMax.rawValue, AllDeviceNames.iPadPro_11.rawValue], id: \.self) { devicesName in
            SampleView()
                .previewDevice(PreviewDevice(rawValue: devicesName))
                .previewDisplayName(devicesName)
        }
    }
}

// Show all iPhones
struct SampleView_Previews_AlliPhones: PreviewProvider {
    static var previews: some View {
        ForEach(iPhoneDeviceNames.all, id: \.self) { devicesName in
            SampleView()
                .previewDevice(PreviewDevice(rawValue: devicesName))
                .previewDisplayName(devicesName)
        }
    }
}

// Show all iPads
struct SampleView_Previews_AlliPads: PreviewProvider {
    static var previews: some View {
        ForEach(iPadDeviceNames.all, id: \.self) { devicesName in
            SampleView()
                .previewDevice(PreviewDevice(rawValue: devicesName))
                .previewDisplayName(devicesName)
        }
    }
}

```

# Helper Extension

```swift

extension View {

    @inlinable public func previewDevice(_ value: AllDeviceNames) -> some View {
        self.previewDevice(PreviewDevice(rawValue: value.rawValue))
    }

}

```
